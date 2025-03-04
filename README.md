# README Report: Hotel Booking Data Analysis

## 1. Overview
This project focuses on analyzing hotel booking data to uncover trends, identify data quality issues, and generate actionable insights. The dataset consists of five CSV files:
- `dim_date.csv`
- `dim_hotels.csv`
- `dim_rooms.csv`
- `fact_aggregated_bookings.csv`
- `fact_bookings.csv`

The analysis is divided into two main phases:
1. **Data Exploration**: Understanding the structure, distribution, and key characteristics of the data.
2. **Data Cleaning**: Addressing data quality issues such as invalid entries and outliers.

### Technology Used
- **Programming Language**: Python
- **Libraries**:
  - **Pandas**: For data manipulation and analysis.
  - **Matplotlib**: For data visualization (e.g., bar plots).
  - **Jupyter Notebook**: For interactive data exploration and documentation.
- **Data Sources**: CSV files containing hotel booking and property data.
- **Key Features**:
  - Data cleaning using statistical methods (e.g., mean and standard deviation for outlier detection).
  - Descriptive statistics and visualization to uncover trends and patterns.

---

## 2. Key Findings

### 2.1 Data Exploration
- **Bookings Data (`fact_bookings.csv`)**:
  - Contains 134,590 rows and 12 columns.
  - Key columns include `booking_id`, `property_id`, `no_guests`, `room_category`, `booking_platform`, `ratings_given`, `booking_status`, `revenue_generated`, and `revenue_realized`.
  - Room categories: `RT1`, `RT2`, `RT3`, `RT4`.
  - Booking platforms: `direct online`, `others`, `logtrip`, `tripster`, `makeyourtrip`, `journey`, `direct offline`.
  - Descriptive statistics reveal:
    - Average number of guests per booking: ~2.
    - Average revenue generated: ~15,378.
    - Average revenue realized: ~12,696.

- **Hotels Data (`dim_hotels.csv`)**:
  - Contains 25 unique properties.
  - Hotel categories: 16 "Luxury" and 9 "Business".
  - Cities with hotels: Primarily `Delhi` and `Mumbai`.

- **Aggregate Bookings Data (`fact_aggregated_bookings.csv`)**:
  - Tracks successful bookings and capacity for each property, room category, and check-in date.
  - Some days show bookings exceeding capacity, indicating potential data errors or overbooking.

### 2.2 Data Cleaning
- **Invalid Guests**:
  - Removed rows where `no_guests` was less than or equal to 0 (invalid entries).
  - Reduced dataset from 134,590 to 134,578 rows.

- **Outlier Removal in Revenue Generated**:
  - Identified and removed outliers in `revenue_generated` using the mean and standard deviation.
  - Rows with `revenue_generated` above the higher limit (294,498) were removed.
  - Dataset reduced to 134,573 rows.

- **Outlier Analysis in Revenue Realized**:
  - Analyzed `revenue_realized` for outliers.
  - Found that higher revenue values were associated with the "RT4" (presidential suite) room category, which is expected due to its luxurious nature.
  - No further cleaning was performed on this column.

- **Missing Values**:
  - The `ratings_given` column has 77,897 missing values, which is reasonable as many customers do not provide ratings.
  - No cleaning was performed on this column.

---

## 3. Insight Generation

### 3.1 Booking Trends
- **Room Category Popularity**:
  - The most common room categories are `RT1` and `RT2`, which are likely standard or mid-tier rooms.
  - `RT4` (presidential suite) has higher revenue but fewer bookings, indicating it caters to a niche, high-spending customer segment.

- **Booking Platforms**:
  - The majority of bookings come from `others` (55,066), followed by `makeyourtrip` (26,898) and `logtrip` (14,756).
  - `direct online` and `direct offline` platforms have fewer bookings, suggesting that third-party platforms dominate the market.

### 3.2 Revenue Insights
- **Revenue Distribution**:
  - The average revenue generated per booking is ~15,378, while the average revenue realized is ~12,696.
  - The difference between generated and realized revenue could be due to cancellations, discounts, or refunds.

- **Presidential Suite (RT4)**:
  - `RT4` rooms generate significantly higher revenue, with an average revenue realized of ~23,439.
  - This suggests that luxury rooms contribute disproportionately to overall revenue despite fewer bookings.

### 3.3 Data Quality Insights
- **Overbooking**:
  - Some days show bookings exceeding capacity, particularly for `RT2` and `RT1` rooms.
  - This could indicate operational inefficiencies or data entry errors.

- **Invalid Entries**:
  - Negative values in `no_guests` were identified and removed, improving data quality.

### 3.4 Customer Behavior
- **Ratings**:
  - A significant portion of customers (77,897) did not provide ratings, which could indicate a lack of engagement or satisfaction.
  - For customers who did rate, the average rating is ~3.62, suggesting moderate satisfaction.

---

## 4. Recommendations
1. **Focus on High-Revenue Segments**:
   - Invest in marketing and upselling strategies for `RT4` (presidential suite) rooms to maximize revenue from high-spending customers.

2. **Improve Booking Platform Performance**:
   - Analyze why third-party platforms like `makeyourtrip` and `logtrip` dominate bookings and explore ways to increase direct bookings.

3. **Address Overbooking**:
   - Investigate days where bookings exceed capacity and implement measures to prevent overbooking.

4. **Enhance Customer Engagement**:
   - Encourage customers to provide ratings by offering incentives or simplifying the rating process.
   - Use feedback to improve service quality and customer satisfaction.

5. **Data Quality Improvements**:
   - Regularly audit the dataset for invalid entries (e.g., negative `no_guests`) and outliers.
   - Implement validation checks during data entry to prevent such issues.

---

## 5. Conclusion
This analysis provides a comprehensive understanding of hotel booking trends, revenue distribution, and customer behavior. By addressing data quality issues and leveraging insights, the hotel chain can optimize operations, improve customer satisfaction, and maximize revenue.


