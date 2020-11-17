-- phpMyAdmin SQL Dump
-- version 4.8.5
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Generation Time: Nov 16, 2020 at 02:05 PM
-- Server version: 10.1.38-MariaDB
-- PHP Version: 7.3.4

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET AUTOCOMMIT = 0;
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Database: `db_billonairebid`
--

-- --------------------------------------------------------

--
-- Table structure for table `admins`
--

CREATE TABLE `admins` (
  `admin_id` int(10) NOT NULL,
  `admin_name` varchar(255) NOT NULL,
  `admin_email` varchar(255) NOT NULL,
  `admin_pass` varchar(255) NOT NULL,
  `admin_image` text NOT NULL,
  `admin_country` text NOT NULL,
  `admin_about` text NOT NULL,
  `admin_contact` varchar(255) NOT NULL,
  `admin_job` varchar(255) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Dumping data for table `admins`
--

INSERT INTO `admins` (`admin_id`, `admin_name`, `admin_email`, `admin_pass`, `admin_image`, `admin_country`, `admin_about`, `admin_contact`, `admin_job`) VALUES
(3, 'emma', 'emma@gmail.com', 'emma', 'images.jpg', 'Ireland', 'Electronic Eng', '22222222', 'Handy Man');

-- --------------------------------------------------------

--
-- Table structure for table `biders`
--

CREATE TABLE `biders` (
  `bider_id` int(10) NOT NULL,
  `bider_name` varchar(255) NOT NULL,
  `bider_email` varchar(255) NOT NULL,
  `bider_pass` varchar(255) NOT NULL,
  `bider_country` text NOT NULL,
  `bider_city` text NOT NULL,
  `bider_contact` varchar(255) NOT NULL,
  `bider_address` text NOT NULL,
  `bider_image` text NOT NULL,
  `bider_ip` varchar(100) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Dumping data for table `biders`
--

INSERT INTO `biders` (`bider_id`, `bider_name`, `bider_email`, `bider_pass`, `bider_country`, `bider_city`, `bider_contact`, `bider_address`, `bider_image`, `bider_ip`) VALUES
(5, 'osita', 'osita@gmail.com', 'obi', 'Ireland', 'Limerick', '22222222', '23 upper', 'images.jpg', '::1');

-- --------------------------------------------------------

--
-- Table structure for table `bider_orders`
--

CREATE TABLE `bider_orders` (
  `order_id` int(10) NOT NULL,
  `bider_id` int(10) NOT NULL,
  `due_amount` int(100) NOT NULL,
  `invoice_no` int(100) NOT NULL,
  `qty` int(10) NOT NULL,
  `order_date` date NOT NULL,
  `order_status` text NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

-- --------------------------------------------------------

--
-- Table structure for table `bid_cart`
--

CREATE TABLE `bid_cart` (
  `p_id` int(10) NOT NULL,
  `ip_add` varchar(255) NOT NULL,
  `qty` int(10) NOT NULL,
  `size` text NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Dumping data for table `bid_cart`
--

INSERT INTO `bid_cart` (`p_id`, `ip_add`, `qty`, `size`) VALUES
(3, '1', 1, '');

-- --------------------------------------------------------

--
-- Table structure for table `bid_categories`
--

CREATE TABLE `bid_categories` (
  `bid_cat_id` int(10) NOT NULL,
  `bid_cat_title` text NOT NULL,
  `bid_cat_desc` text NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Dumping data for table `bid_categories`
--

INSERT INTO `bid_categories` (`bid_cat_id`, `bid_cat_title`, `bid_cat_desc`) VALUES
(1, 'Electronics', 'laptops'),
(2, 'Clothes', 'laptops'),
(3, 'Plant Machinery', 'laptops'),
(4, 'Books', 'laptops');

-- --------------------------------------------------------

--
-- Table structure for table `bid_pending_orders`
--

CREATE TABLE `bid_pending_orders` (
  `order_id` int(10) NOT NULL,
  `bider_id` int(10) NOT NULL,
  `invoice_no` int(10) NOT NULL,
  `bid_product_id` text NOT NULL,
  `qty` int(10) NOT NULL,
  `order_status` text NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Dumping data for table `bid_pending_orders`
--

INSERT INTO `bid_pending_orders` (`order_id`, `bider_id`, `invoice_no`, `bid_product_id`, `qty`, `order_status`) VALUES
(1, 4, 616256572, '2', 1, 'Complete'),
(2, 4, 616256572, '6', 1, 'pending'),
(3, 4, 616256572, '16', 1, 'pending');

-- --------------------------------------------------------

--
-- Table structure for table `bid_products`
--

CREATE TABLE `bid_products` (
  `bid_product_id` int(10) NOT NULL,
  `bid_p_cat_id` int(10) NOT NULL,
  `bid_cat_id` int(10) NOT NULL,
  `date` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `bid_product_title` text NOT NULL,
  `bid_product_img1` text NOT NULL,
  `bid_product_img2` text NOT NULL,
  `bid_product_img3` text NOT NULL,
  `bid_product_price` int(10) NOT NULL,
  `bid_product_keywords` text NOT NULL,
  `bid_product_desc` text NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Dumping data for table `bid_products`
--

INSERT INTO `bid_products` (`bid_product_id`, `bid_p_cat_id`, `bid_cat_id`, `date`, `bid_product_title`, `bid_product_img1`, `bid_product_img2`, `bid_product_img3`, `bid_product_price`, `bid_product_keywords`, `bid_product_desc`) VALUES
(1, 1, 2, '2020-11-14 11:40:33', 'Hp Dv 2000', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 66, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(2, 4, 3, '2020-11-14 12:25:06', 'Biafra War ', '51sAIXwN9sL._SX331_BO1,204,203,200_.jpg', '51sAIXwN9sL._SX331_BO1,204,203,200_.jpg', '51sAIXwN9sL._SX331_BO1,204,203,200_.jpg', 121, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(3, 5, 2, '2020-11-14 13:53:14', 'Girl Polos T-Shirt', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 55, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(4, 1, 1, '2020-11-14 11:41:42', 'Lenovo 344NX', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 100, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(5, 1, 2, '2020-11-14 11:58:13', 'Acer VBS-560', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 103, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(6, 4, 2, '2020-11-14 12:21:07', 'Biafra Genocide', 'biafra_war1.jpg', 'biafra_war1.jpg', 'biafra_war1.jpg', 211, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(7, 3, 2, '2020-11-14 12:06:39', 'High Heels Pantofel Brukat', 'printed-trousers-womens-537485_l.jpg', 'printed-trousers-womens-537485_l.jpg', 'printed-trousers-womens-537485_l.jpg', 45, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(8, 3, 1, '2020-11-14 12:06:49', 'Dell S200 Vistro', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 51, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(9, 2, 1, '2020-11-14 12:07:10', 'Smasung NP-5000', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 166, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(10, 2, 2, '2020-11-14 12:07:22', 'Diamond Heart Ring', 'printed-trousers-womens-537485_l.jpg', 'printed-trousers-womens-537485_l.jpg', 'printed-trousers-womens-537485_l.jpg', 300, 'Cheap To Bid', '<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Tenetur cupiditate animi, voluptas neque quasi qui unde fuga porro vero magnam maiores optio amet quos temporibus? Amet saepe fugit nostrum a?</p>The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(11, 5, 1, '2020-11-14 12:07:34', 'Dell Inspiron X900', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 50, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(12, 5, 1, '2020-11-14 12:07:53', 'HP Envy 1000', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 45, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(13, 5, 1, '2020-11-14 12:08:06', 'MacBook Pro A1214', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 40, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(14, 1, 1, '2020-11-14 12:08:22', 'Toshia DEL-7000', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 98, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(15, 1, 1, '2020-11-14 12:08:33', 'MacBook Pro DA2020', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 90, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.'),
(16, 1, 2, '2020-11-14 12:09:04', 'Acer PPN-2020', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 'laptop_hp_1E6T5EA.jpg', 99, 'Cheap To Bid', 'The E406 is designed to help you be productive all day - even when you\'re on the move. This compact and lightweight 14-inch laptop is powered by the latest Intel processor and provides long-lasting battery life. And with a NanoEdge display for immersive viewing, it\'s the best laptop for people on the go.');

-- --------------------------------------------------------

--
-- Table structure for table `bid_product_categories`
--

CREATE TABLE `bid_product_categories` (
  `bid_p_cat_id` int(10) NOT NULL,
  `bid_p_cat_title` text NOT NULL,
  `bid_p_cat_desc` text NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Dumping data for table `bid_product_categories`
--

INSERT INTO `bid_product_categories` (`bid_p_cat_id`, `bid_p_cat_title`, `bid_p_cat_desc`) VALUES
(1, 'Laptops', 'laptops'),
(2, 'Shoes', 'laptops'),
(3, 'Trailers', 'laptops'),
(4, 'Histroy Books', 'laptops'),
(5, 'T-Shirt', 'laptops');

-- --------------------------------------------------------

--
-- Table structure for table `bid_slider`
--

CREATE TABLE `bid_slider` (
  `bid_slide_id` int(10) NOT NULL,
  `bid_slide_name` varchar(255) NOT NULL,
  `bid_slide_image` text NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Dumping data for table `bid_slider`
--

INSERT INTO `bid_slider` (`bid_slide_id`, `bid_slide_name`, `bid_slide_image`) VALUES
(1, 'slide-13', 'slide-13.jpg'),
(2, 'slide-13', 'slide-13.jpg'),
(3, 'slide-13', 'slide-13.jpg'),
(4, 'slide-13', 'slide-13.jpg');

-- --------------------------------------------------------

--
-- Table structure for table `payments`
--

CREATE TABLE `payments` (
  `payment_id` int(10) NOT NULL,
  `invoice_no` int(10) NOT NULL,
  `amount` int(10) NOT NULL,
  `payment_mode` text NOT NULL,
  `ref_no` int(10) NOT NULL,
  `code` int(10) NOT NULL,
  `payment_date` text NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

--
-- Indexes for dumped tables
--

--
-- Indexes for table `admins`
--
ALTER TABLE `admins`
  ADD PRIMARY KEY (`admin_id`);

--
-- Indexes for table `biders`
--
ALTER TABLE `biders`
  ADD PRIMARY KEY (`bider_id`);

--
-- Indexes for table `bider_orders`
--
ALTER TABLE `bider_orders`
  ADD PRIMARY KEY (`order_id`);

--
-- Indexes for table `bid_cart`
--
ALTER TABLE `bid_cart`
  ADD PRIMARY KEY (`p_id`);

--
-- Indexes for table `bid_categories`
--
ALTER TABLE `bid_categories`
  ADD PRIMARY KEY (`bid_cat_id`);

--
-- Indexes for table `bid_pending_orders`
--
ALTER TABLE `bid_pending_orders`
  ADD PRIMARY KEY (`order_id`);

--
-- Indexes for table `bid_products`
--
ALTER TABLE `bid_products`
  ADD PRIMARY KEY (`bid_product_id`);

--
-- Indexes for table `bid_product_categories`
--
ALTER TABLE `bid_product_categories`
  ADD PRIMARY KEY (`bid_p_cat_id`);

--
-- Indexes for table `bid_slider`
--
ALTER TABLE `bid_slider`
  ADD PRIMARY KEY (`bid_slide_id`);

--
-- Indexes for table `payments`
--
ALTER TABLE `payments`
  ADD PRIMARY KEY (`payment_id`);

--
-- AUTO_INCREMENT for dumped tables
--

--
-- AUTO_INCREMENT for table `admins`
--
ALTER TABLE `admins`
  MODIFY `admin_id` int(10) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- AUTO_INCREMENT for table `biders`
--
ALTER TABLE `biders`
  MODIFY `bider_id` int(10) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=6;

--
-- AUTO_INCREMENT for table `bider_orders`
--
ALTER TABLE `bider_orders`
  MODIFY `order_id` int(10) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `bid_categories`
--
ALTER TABLE `bid_categories`
  MODIFY `bid_cat_id` int(10) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;

--
-- AUTO_INCREMENT for table `bid_pending_orders`
--
ALTER TABLE `bid_pending_orders`
  MODIFY `order_id` int(10) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- AUTO_INCREMENT for table `bid_products`
--
ALTER TABLE `bid_products`
  MODIFY `bid_product_id` int(10) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=17;

--
-- AUTO_INCREMENT for table `bid_product_categories`
--
ALTER TABLE `bid_product_categories`
  MODIFY `bid_p_cat_id` int(10) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=6;

--
-- AUTO_INCREMENT for table `payments`
--
ALTER TABLE `payments`
  MODIFY `payment_id` int(10) NOT NULL AUTO_INCREMENT;
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;

