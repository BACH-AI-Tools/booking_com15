# Booking Com15 MCP Server

[English](./README_EN.md) | 简体中文 | [繁體中文](./README_ZH-TW.md)

## 🚀 使用 EMCP 平台快速体验

**[EMCP](https://sit-emcp.kaleido.guru)** 是一个强大的 MCP 服务器管理平台，让您无需手动配置即可快速使用各种 MCP 服务器！

### 快速开始：

1. 🌐 访问 **[EMCP 平台](https://sit-emcp.kaleido.guru)**
2. 📝 注册并登录账号
3. 🎯 进入 **MCP 广场**，浏览所有可用的 MCP 服务器
4. 🔍 搜索或找到本服务器（`bach-booking_com15`）
5. 🎉 点击 **"安装 MCP"** 按钮
6. ✅ 完成！即可在您的应用中使用

### EMCP 平台优势：

- ✨ **零配置**：无需手动编辑配置文件
- 🎨 **可视化管理**：图形界面轻松管理所有 MCP 服务器
- 🔐 **安全可靠**：统一管理 API 密钥和认证信息
- 🚀 **一键安装**：MCP 广场提供丰富的服务器选择
- 📊 **使用统计**：实时查看服务调用情况

立即访问 **[EMCP 平台](https://sit-emcp.kaleido.guru)** 开始您的 MCP 之旅！


---

## 简介

这是一个使用 [FastMCP](https://fastmcp.wiki) 自动生成的 MCP 服务器，用于访问 Booking Com15 API。

- **PyPI 包名**: `bach-booking_com15`
- **版本**: 1.0.0
- **传输协议**: stdio


## 安装

### 从 PyPI 安装:

```bash
pip install bach-booking_com15
```

### 从源码安装:

```bash
pip install -e .
```

## 运行

### 方式 1: 使用 uvx（推荐，无需安装）

```bash
# 运行（uvx 会自动安装并运行）
uvx --from bach-booking_com15 bach_booking_com15

# 或指定版本
uvx --from bach-booking_com15@latest bach_booking_com15
```

### 方式 2: 直接运行（开发模式）

```bash
python server.py
```

### 方式 3: 安装后作为命令运行

```bash
# 安装
pip install bach-booking_com15

# 运行（命令名使用下划线）
bach_booking_com15
```

## 配置

### API 认证

此 API 需要认证。请设置环境变量:

```bash
export API_KEY="your_api_key_here"
```

### 环境变量

| 变量名 | 说明 | 必需 |
|--------|------|------|
| `API_KEY` | API 密钥 | 是 |
| `PORT` | 不适用 | 否 |
| `HOST` | 不适用 | 否 |



### 在 Claude Desktop 中使用

编辑 Claude Desktop 配置文件 `claude_desktop_config.json`:


```json
{
  "mcpServers": {
    "booking_com15": {
      "command": "python",
      "args": ["E:\path\to\booking_com15\server.py"],
      "env": {
        "API_KEY": "your_api_key_here"
      }
    }
  }
}
```

**注意**: 请将 `E:\path\to\booking_com15\server.py` 替换为实际的服务器文件路径。


## 可用工具

此服务器提供以下工具:


### `search_car_rentals`

-

**端点**: `GET /api/v1/cars/searchCarRentals`


**参数**:

- `pick_up_latitude` (number) *必需*: The pick up location's latitude. pick_up_latitude can be retrieved from api/v1/cars/searchDestination(Search Car Location) endpoint in Car Rental collection as latitude inside coordinates object.

- `pick_up_longitude` (number) *必需*: The pick up location's longitude. pick_up_longitude can be retrieved from api/v1/cars/searchDestination(Search Car Location) endpoint in Car Rental collection as longitude inside coordinates object.

- `drop_off_latitude` (number) *必需*: The drop off location's latitude. drop_off_latitude can be retrieved from api/v1/cars/searchDestination(Search Car Location) endpoint in Car Rental collection as latitude inside coordinates object.

- `drop_off_longitude` (number) *必需*: The drop off location's longitude. drop_off_longitude can be retrieved from api/v1/cars/searchDestination(Search Car Location) endpoint in Car Rental collection as longitude inside coordinates object.

- `pick_up_date` (string) *必需*: Pick up date Format: YYYY-MM-DD

- `drop_off_date` (string) *必需*: Drop off date Format: YYYY-MM-DD

- `pick_up_time` (string) *必需*: Pick up time Format: HH:MM Note: The format of time is 24 hours.

- `drop_off_time` (string) *必需*: Drop off time Format: HH:MM Note: The format of time is 24 hours.

- `driver_age` (number): The driver's age. The default value is set to 30. Note: The driver age must be in the range of 20 to 65 years.

- `filters` (string): Used to refine search results based on specific suppliers, car categories, or other attributes. Multiple filters can be applied by passing them as a comma-separated list in the following format: :: For example: supplier::Avis,supplier::Budget,carCategory::medium,carCategory::large This will return results from Avis and Budget, and only cars in the medium and large categories. To discover available filters, make a request to the /api/v1/cars/searchCarRentals endpoint and refer to the data → filte

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.

- `location` (string): location can be retrieved from api/v1/meta/getLocations(Get Location) endpoint in Meta collection.



---


### `search_flights`

-

**端点**: `GET /api/v1/flights/searchFlights`


**参数**:

- `fromId` (string) *必需*: From/Departure location Id. fromId can be retrieved from api/v1/flights/searchDestination(Search Flight Location) endpoint in Flights collection as id.

- `toId` (string) *必需*: To/Arrival location Id. toId can be retrieved from api/v1/flights/searchDestination(Search Flight Location) endpoint in Flights collection as id.

- `departDate` (string) *必需*: Departure or travel date. Format: YYYY-MM-DD

- `returnDate` (string): Return date. Format: YYYY-MM-DD

- `stops` (string): Filters flights based on the number of stops. Accepted values are: none for no preference (returns flights with any number of stops) 0 for non-stop flights 1 for one-stop flights 2 for two-stop flights If provided, the value must be either none, 0, 1, or 2.

- `pageNo` (number): The page number.

- `adults` (number): The number of guests who are 18 years of age or older. The default value is set to 1.

- `children` (string): The number of children, including infants, who are under 18. Example: Child 1 Age = 8 months Child 2 Age = 1 year Child 3 Age = 17 years Here is what the request parameter would look like: children_age: 0,1,17

- `sort` (string): This parameter orders result by BEST, CHEAPEST or FASTEST flights.

- `cabinClass` (string): Search for flights that match the cabin class specified. Cabin call can be either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `search_hotels_by_coordinates`

-

**端点**: `GET /api/v1/hotels/searchHotelsByCoordinates`


**参数**:

- `latitude` (string) *必需*: Latitude of the searched location. latitude can be retrieved from api/v1/meta/locationToLatLong(Location to Lat Long) endpoint in Meta collection.

- `longitude` (string) *必需*: Longitude of the searched location. longitude can be retrieved from api/v1/meta/locationToLatLong(Location to Lat Long) endpoint in Meta collection.

- `arrival_date` (string) *必需*: The date on which you will arrive or check-in

- `departure_date` (string) *必需*: The date of departure or check-out.

- `radius` (number): The hotels that are within the radius. The radius is measured in kilometers. Default is set to 100. Range is between 10 to 500.

- `adults` (number): The number of guests who are 18 years of age or older. The default value is set to 1.

- `children_age` (string): The number of children, including infants, who are under 18. Example: Child 1 Age = 8 months Child 2 Age = 1 year Child 3 Age = 17 years Here is what the request parameter would look like: children_age: 0,1,17

- `room_qty` (number): The number of rooms that are required. The default value is set to 1.

- `price_min` (number): Minimum Price filter for search.

- `price_max` (number): Maximum Price filter for search.

- `units` (string): The measurement of distance in metric or imperial.

- `page_number` (string): Example value: 1

- `temperature_unit` (string): The temperature unit in Fahrenheit or Celsius. c = Celsius f = Fahrenheit

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.

- `location` (string): location can be retrieved from api/v1/meta/getLocations(Get Location) endpoint in Meta collection.



---


### `search_hotels`

-

**端点**: `GET /api/v1/hotels/searchHotels`


**参数**:

- `dest_id` (number) *必需*: dest_id can be retrieved from api/v1/hotels/searchDestination(Search Hotel Destination) endpoint in Hotels collection.

- `search_type` (string) *必需*: search_type can be retrieved from api/v1/hotels/searchDestination(Search Hotel Destination) endpoint in Hotels collection.

- `arrival_date` (string) *必需*: The date on which you will arrive or check-in

- `departure_date` (string) *必需*: The date of departure or check-out.

- `adults` (number): The number of guests who are 18 years of age or older. The default value is set to 1.

- `children_age` (string): The number of children, including infants, who are under 18. Example: Child 1 Age = 8 months Child 2 Age = 1 year Child 3 Age = 17 years Here is what the request parameter would look like: children_age: 0,1,17

- `room_qty` (number): The number of rooms that are required. The default value is set to 1.

- `page_number` (number): The page number.

- `price_min` (number): Minimum Price filter for search.

- `price_max` (number): Maximum Price filter for search.

- `sort_by` (string): sort_by can be retrieved from api/v1/hotels/getSortBy(Get Sort By) endpoint in Hotels collection.

- `categories_filter` (string): categories_filter can be retrieved from api/v1/hotels/getFilter(Get Filter) endpoint in Hotels collection.

- `units` (string): The measurement of distance in metric or imperial.

- `temperature_unit` (string): The temperature unit in Fahrenheit or Celsius. c = Celsius f = Fahrenheit

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.

- `location` (string): location can be retrieved from api/v1/meta/getLocations(Get Location) endpoint in Meta collection.



---


### `get_room_list_with_availability`

-

**端点**: `GET /api/v1/hotels/getRoomListWithAvailability`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `arrival_date` (string) *必需*: The date on which you will arrive or check-in

- `departure_date` (string) *必需*: The date of departure or check-out.

- `adults` (number): The number of guests who are 18 years of age or older. The default value is set to 1.

- `children_age` (string): The number of children, including infants, who are under 18. Example: Child 1 Age = 8 months Child 2 Age = 1 year Child 3 Age = 17 years Here is what the request parameter would look like: children_age: 0,1,17

- `room_qty` (number): The number of rooms that are required. The default value is set to 1.

- `units` (string): The measurement of distance in metric or imperial.

- `temperature_unit` (string): The temperature unit in Fahrenheit or Celsius. c = Celsius f = Fahrenheit

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.

- `location` (string): location can be retrieved from api/v1/meta/getLocations(Get Location) endpoint in Meta collection.



---


### `get_room_list`

-

**端点**: `GET /api/v1/hotels/getRoomList`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `arrival_date` (string) *必需*: The date on which you will arrive or check-in

- `departure_date` (string) *必需*: The date of departure or check-out.

- `adults` (number): The number of guests who are 18 years of age or older. The default value is set to 1.

- `children_age` (string): The number of children, including infants, who are under 18. Example: Child 1 Age = 8 months Child 2 Age = 1 year Child 3 Age = 17 years Here is what the request parameter would look like: children_age: 0,1,17

- `room_qty` (number): The number of rooms that are required. The default value is set to 1.

- `units` (string): The measurement of distance in metric or imperial.

- `temperature_unit` (string): The temperature unit in Fahrenheit or Celsius. c = Celsius f = Fahrenheit

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.

- `location` (string): location can be retrieved from api/v1/meta/getLocations(Get Location) endpoint in Meta collection.



---


### `get_room_availability`

Check for availability on future dates.

**端点**: `GET /api/v1/hotels/getAvailability`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `min_date` (string) *必需*: The starting date range.

- `max_date` (string) *必需*: The ending date range

- `room_qty` (number): The number of rooms that are required. The default value is set to 1.

- `adults` (number): The number of guests who are 18 years of age or older. The default value is set to 1.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.

- `location` (string): location can be retrieved from api/v1/meta/getLocations(Get Location) endpoint in Meta collection.



---


### `get_currency`

Get the list of currencies that are available.

**端点**: `GET /api/v1/meta/getCurrency`



---


### `get_exchange_rates`

Obtain a list of exchange rates for all currencies utilizing the base currency.

**端点**: `GET /api/v1/meta/getExchangeRates`


**参数**:

- `base_currency` (string) *必需*: Base currency.



---


### `test_api`

To check if server is up and running

**端点**: `GET /api/v1/test`



---


### `get_languages`

-

**端点**: `GET /api/v1/meta/getLanguages`



---


### `get_location`

-

**端点**: `GET /api/v1/meta/getLocations`



---


### `get_attraction_reviews`

Retrieves reviews for a specified attraction, including user ratings, comments, and review counts.

**端点**: `GET /api/v1/attraction/getAttractionReviews`


**参数**:

- `id` (string) *必需*: id can be retrieved from api/v1/attraction/searchAttractions(Search Attractions) endpoint in Attraction collection as id inside products (data->products->id)

- `page` (number): The page number.



---


### `search_attractions`

-

**端点**: `GET /api/v1/attraction/searchAttractions`


**参数**:

- `id` (string) *必需*: id can be retrieved from api/v1/attraction/searchLocation(Search Attraction Location) endpoint in Attraction collection as id inside products or destinations.

- `startDate` (string): Sort the data by the start date.

- `endDate` (string): Sort the data by the end date.

- `sortBy` (string): This parameter orders result by trending, attr_book_score or lowest_price.

- `page` (number): The page number.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `typeFilters` (string): typeFilters can be retrieved from /api/v1/attraction/searchAttractions(Search Attractions) endpoint in Hotels collection. data->filterOptions-> typeFilters[]-> tagname. Note:- typeFilters should be separated by commas if passing multiple values. Example: tag1,tag2,tag

- `priceFilters` (string): priceFilters can be retrieved from /api/v1/attraction/searchAttractions(Search Attractions) endpoint in Hotels collection. data->filterOptions-> priceFilters[]-> tagname. Note:- priceFilters should be separated by commas if passing multiple values. Example: tag1,tag2,tag

- `ufiFilters` (string): ufiFilters can be retrieved from /api/v1/attraction/searchAttractions(Search Attractions) endpoint in Hotels collection. data->filterOptions-> ufiFilters[]-> tagname. Note:- ufiFilters should be separated by commas if passing multiple values. Example: tag1,tag2,tag

- `labelFilters` (string): labelFilters can be retrieved from /api/v1/attraction/searchAttractions(Search Attractions) endpoint in Hotels collection. data->filterOptions-> labelFilters[]-> tagname. Note:- labelFilters should be separated by commas if passing multiple values. Example: tag1,tag2,tag



---


### `get_hotel_facilities`

-

**端点**: `GET /api/v1/hotels/getHotelFacilities`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `arrival_date` (string): The date on which you will arrive or check-in

- `departure_date` (string): The date of departure or check-out.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_hotel_photos`

-

**端点**: `GET /api/v1/hotels/getHotelPhotos`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.



---


### `get_question_and_answer`

-

**端点**: `GET /api/v1/hotels/getQuestionAndAnswer`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_nearby_cities`

-

**端点**: `GET /api/v1/hotels/getNearbyCities`


**参数**:

- `latitude` (string) *必需*: Latitude of the searched location. latitude can be retrieved from api/v1/meta/locationToLatLong(Location to Lat Long) endpoint in Meta collection.

- `longitude` (string) *必需*: Longitude of the searched location. longitude can be retrieved from api/v1/meta/locationToLatLong(Location to Lat Long) endpoint in Meta collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_popular_attraction_near_by`

-

**端点**: `GET /api/v1/hotels/getPopularAttractionNearBy`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_hotel_reviewstips`

-

**端点**: `GET /api/v1/hotels/getHotelReviews`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `sort_option_id` (string): sort_option_id can be retrieved from api/v1/hotels/getHotelReviewsSortOption(Get Hotel Reviews(Tips) Sort Option) endpoint in Hotels collection.

- `page_number` (number): The page number.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_hotel_reviewstips_sort_option`

Obtain all the available sort parameters for hotel reviews.

**端点**: `GET /api/v1/hotels/getHotelReviewsSortOption`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_hotel_review_scores`

-

**端点**: `GET /api/v1/hotels/getHotelReviewScores`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_hotel_reviews_filter_metadata`

-

**端点**: `GET /api/v1/hotels/getHotelReviewsFilterMetadata`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `property_children_policies`

-

**端点**: `GET /api/v1/hotels/propertyChildrenPolicies`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_hotel_policies`

-

**端点**: `GET /api/v1/hotels/getHotelPolicies`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_description_and_info`

-

**端点**: `GET /api/v1/hotels/getDescriptionAndInfo`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_hotel_details`

-

**端点**: `GET /api/v1/hotels/getHotelDetails`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `arrival_date` (string) *必需*: The date on which you will arrive or check-in

- `departure_date` (string) *必需*: The date of departure or check-out.

- `adults` (number): The number of guests who are 18 years of age or older. The default value is set to 1.

- `children_age` (string): The number of children, including infants, who are under 18. Example: Child 1 Age = 8 months Child 2 Age = 1 year Child 3 Age = 17 years Here is what the request parameter would look like: children_age: 0,1,17

- `room_qty` (number): The number of rooms that are required. The default value is set to 1.

- `units` (string): The measurement of distance in metric or imperial.

- `temperature_unit` (string): The temperature unit in Fahrenheit or Celsius. c = Celsius f = Fahrenheit

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `get_filter`

-

**端点**: `GET /api/v1/hotels/getFilter`


**参数**:

- `dest_id` (string) *必需*: dest_id can be retrieved from api/v1/hotels/searchDestination(Search Hotel Destination) endpoint in Hotels collection.

- `search_type` (string) *必需*: search_type can be retrieved from api/v1/hotels/searchDestination(Search Hotel Destination) endpoint in hotel collection.

- `arrival_date` (string) *必需*: The date on which you will arrive or check-in

- `departure_date` (string) *必需*: The date of departure or check-out.

- `adults` (number): The number of guests who are 18 years of age or older. The default value is set to 1.

- `children_age` (string): The number of children, including infants, who are under 18. Example: Child 1 Age = 8 months Child 2 Age = 1 year Child 3 Age = 17 years Here is what the request parameter would look like: children_age: 0,1,17

- `room_qty` (number): The number of rooms that are required. The default value is set to 1.

- `categories_filter` (string): categories_filter can be retrieved from api/v1/hotels/getFilter(Get Filter) endpoint in Hotels collection. Note: For the initial request, leave it blank.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `search_hotel_destination`

-

**端点**: `GET /api/v1/hotels/searchDestination`


**参数**:

- `query` (string) *必需*: Names of locations, cities, districts, places, countries, counties etc.



---


### `search_car_location`

Find locations by searching for their name, address, city, state, country, etc.

**端点**: `GET /api/v1/cars/searchDestination`


**参数**:

- `query` (string) *必需*: Names of locations, cities, districts, places, countries, counties etc.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `location_to_lat_long`

Get location/address latitude and longitude

**端点**: `GET /api/v1/meta/locationToLatLong`


**参数**:

- `query` (string) *必需*: Names of locations, apartment, address, cities, districts, places, countries, counties etc.



---


### `get_attraction_details`

-

**端点**: `GET /api/v1/attraction/getAttractionDetails`


**参数**:

- `slug` (string) *必需*: slug can be retrieved from api/v1/attraction/searchLocation(Search Attraction Location) endpoint in Attraction collection as productSlug inside products or destinations.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `get_min_price_multi_stops`

-

**端点**: `GET /api/v1/flights/getMinPriceMultiStops`


**参数**:

- `legs` (string) *必需*: The legs must contain the fromId, toId and date in object format and must be passed in an array. EXAMPLE: [ { 'fromId': 'BOM.AIRPORT', 'toId': 'AMD.AIRPORT', 'date': '2024-05-25' }, … ] Note: If there are multiple stops, there should be more leg objects in the array.

- `cabinClass` (string): Search for flights that match the cabin class specified. Cabin call can be either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `get_sort_by`

-

**端点**: `GET /api/v1/hotels/getSortBy`


**参数**:

- `dest_id` (string) *必需*: dest_id can be retrieved from api/v1/hotels/searchDestination(Search Hotel Destination) endpoint in Hotels collection.

- `search_type` (string) *必需*: search_type can be retrieved from api/v1/hotels/searchDestination(Search Hotel Destination) endpoint in Hotels collection.

- `arrival_date` (string) *必需*: The date on which you will arrive or check-in

- `departure_date` (string) *必需*: The date of departure or check-out.

- `adults` (number): The number of guests who are 18 years of age or older. The default value is set to 1.

- `children_age` (string): The number of children, including infants, who are under 18. Example: Child 1 Age = 8 months Child 2 Age = 1 year Child 3 Age = 17 years Here is what the request parameter would look like: children_age: 0,1,17

- `room_qty` (number): The number of rooms that are required. The default value is set to 1.

- `categories_filter` (string): categories_filter can be retrieved from api/v1/hotels/getFilter(Get Filter) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `search_taxi`

-

**端点**: `GET /api/v1/taxi/searchTaxi`


**参数**:

- `pick_up_place_id` (string) *必需*: The pick up location's place id. pick_up_place_id can be retrieved from api/v1/taxi/searchLocation(Taxi Search Location) endpoint in Taxi collection as googlePlaceId.

- `drop_off_place_id` (string) *必需*: The drop off location's place id. drop_off_place_id can be retrieved from api/v1/taxi/searchLocation(Taxi Search Location) endpoint in Taxi collection as googlePlaceId.

- `pick_up_date` (string) *必需*: Pick up date Format: YYYY-MM-DD

- `pick_up_time` (string) *必需*: Pick up time Format: HH:MM Note: The format of time is 24 hours.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `booking_summary`

-

**端点**: `GET /api/v1/cars/bookingSummary`


**参数**:

- `vehicle_id` (string) *必需*: Vehicle ID. vehicle_id can be retrieved from api/v1/cars/searchCarRentals(Search Car Rentals) endpoint in Car Rental collection as vehicle_id inside search_results object.

- `search_key` (string) *必需*: search_key can be retrieved from api/v1/cars/searchCarRentals(Search Car Rentals) endpoint in Car Rental collection as search_key.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `vehicle_supplier_ratings`

-

**端点**: `GET /api/v1/cars/vehicleSupplierRatings`


**参数**:

- `vehicle_id` (string) *必需*: Vehicle ID. vehicle_id can be retrieved from api/v1/cars/searchCarRentals(Search Car Rentals) endpoint in Car Rental collection as vehicle_id inside search_results object.

- `search_key` (string) *必需*: search_key can be retrieved from api/v1/cars/searchCarRentals(Search Car Rentals) endpoint in Car Rental collection as search_key.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `get_flight_details`

-

**端点**: `GET /api/v1/flights/getFlightDetails`


**参数**:

- `token` (string) *必需*: token can be retrieved from api/v1/flights/searchFlights(Search Flights) or api/v1/flights/searchFlightsMultiStops(Search Flights Multi Stops) endpoints in Flights collection as token.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `get_min_price`

-

**端点**: `GET /api/v1/flights/getMinPrice`


**参数**:

- `fromId` (string) *必需*: From/Departure location Id. fromId can be retrieved from api/v1/flights/searchDestination(Search Flight Location) endpoint in Flights collection as id.

- `toId` (string) *必需*: To/Arrival location Id. toId can be retrieved from api/v1/flights/searchDestination(Search Flight Location) endpoint in Flights collection as id.

- `departDate` (string) *必需*: Departure or travel date. Format: YYYY-MM-DD

- `returnDate` (string): Return date. Format: YYYY-MM-DD

- `cabinClass` (string): Search for flights that match the cabin class specified. Cabin call can be either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `payment_features_of_the_hotel`

-

**端点**: `GET /api/v1/hotels/getPaymentFeatures`


**参数**:

- `hotel_id` (string) *必需*: hotel_id can be retrieved from api/v1/hotels/searchHotels(Search Hotels) or api/v1/hotels/searchHotelsByCoordinates(Search Hotels By Coordinates ) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `taxi_search_location`

-

**端点**: `GET /api/v1/taxi/searchLocation`


**参数**:

- `query` (string) *必需*: Names of locations, cities, districts, places, countries, counties etc.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_availability_calendar`

-

**端点**: `GET /api/v1/attraction/getAvailabilityCalendar`


**参数**:

- `id` (string) *必需*: id can be retrieved from api/v1/attraction/searchLocation(Search Attraction Location) endpoint in Attraction collection as id inside products or destinations.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_availability`

-

**端点**: `GET /api/v1/attraction/getAvailability`


**参数**:

- `slug` (string) *必需*: slug can be retrieved from api/v1/attraction/searchLocation(Search Attraction Location) endpoint in Attraction collection as productSlug inside products or destinations.

- `date` (string): The availability of the data.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `search_attraction_location`

-

**端点**: `GET /api/v1/attraction/searchLocation`


**参数**:

- `query` (string) *必需*: Names of locations, cities, districts, places, countries, counties etc.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `vehicle_details`

-

**端点**: `GET /api/v1/cars/vehicleDetails`


**参数**:

- `vehicle_id` (string) *必需*: Vehicle ID. vehicle_id can be retrieved from api/v1/cars/searchCarRentals(Search Car Rentals) endpoint in Car Rental collection as vehicle_id inside search_results object.

- `search_key` (string) *必需*: search_key can be retrieved from api/v1/cars/searchCarRentals(Search Car Rentals) endpoint in Car Rental collection as search_key.

- `units` (string): The measurement of distance in metric or imperial.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `vehicle_supplier_details`

-

**端点**: `GET /api/v1/cars/vehicleSupplierDetails`


**参数**:

- `vehicle_id` (string) *必需*: Vehicle ID. vehicle_id can be retrieved from api/v1/cars/searchCarRentals(Search Car Rentals) endpoint in Car Rental collection as vehicle_id inside search_results object.

- `search_key` (string) *必需*: Example value: eyJkcml2ZXJzQWdlIjozMCwiZHJvcE9mZkRhdGVUaW1lIjoiMjAyMy0xMS0xN1QxMDowMDowMCIsImRyb3BPZmZMb2NhdGlvbiI6IjQwLjYzOTcwMTg0MzI2MTcsLTczLjc3OTE5NzY5Mjg3MTEiLCJkcm9wT2ZmTG9jYXRpb25UeXBlIjoiTEFUTE9ORyIsInBpY2tVcERhdGVUaW1lIjoiMjAyMy0xMS0xNVQxMDowMDowMCIsInBpY2tVcExvY2F0aW9uIjoiNDAuNjM5NzAxODQzMjYxNywtNzMuNzc5MTk3NjkyODcxMSIsInBpY2tVcExvY2F0aW9uVHlwZSI6IkxBVExPTkciLCJyZW50YWxEdXJhdGlvbkluRGF5cyI6Miwic2VydmljZUZlYXR1cmVzIjpbIk5PX09QQVFVRVMiLCJTVVBSRVNTX0ZJWEVEX1BSSUNFX1ZFSElDTEVTIl19

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `get_packages`

-

**端点**: `GET /api/v1/cars/getPackages`


**参数**:

- `vehicle_id` (string) *必需*: Vehicle ID. vehicle_id can be retrieved from api/v1/cars/searchCarRentals(Search Car Rentals) endpoint in Car Rental collection as vehicle_id inside search_results object.

- `search_key` (string) *必需*: search_key can be retrieved from api/v1/cars/searchCarRentals(Search Car Rentals) endpoint in Car Rental collection as search_key.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `vehicle_supplier_review`

-

**端点**: `GET /api/v1/cars/vehicleSupplierReview`


**参数**:

- `vehicle_id` (string) *必需*: Vehicle ID. vehicle_id can be retrieved from api/v1/cars/searchCarRentals(Search Car Rentals) endpoint in Car Rental collection as vehicle_id inside search_results object.

- `search_key` (string) *必需*: search_key can be retrieved from api/v1/cars/searchCarRentals(Search Car Rentals) endpoint in Car Rental collection as search_key.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---


### `get_seat_map`

-

**端点**: `GET /api/v1/flights/getSeatMap`


**参数**:

- `offerToken` (string) *必需*: offerToken can be retrieved from api/v1/flights/searchFlights(Search Flights) or api/v1/flights/searchFlightsMultiStops(Search Flights Multi Stops) endpoints in Flights collection as offerToken.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `search_flights_multi_stops`

-

**端点**: `GET /api/v1/flights/searchFlightsMultiStops`


**参数**:

- `legs` (string) *必需*: The legs must contain the fromId, toId and date in object format and must be passed in an array. EXAMPLE: [ { 'fromId': 'BOM.AIRPORT', 'toId': 'AMD.AIRPORT', 'date': '2024-05-25' }, … ] Note: If there are multiple stops, there should be more leg objects in the array.

- `pageNo` (number): The page number.

- `adults` (number): The number of guests who are 18 years of age or older. The default value is set to 1.

- `children` (string): The number of children, including infants, who are under 18. Example: Child 1 Age = 8 months Child 2 Age = 1 year Child 3 Age = 17 years Here is what the request parameter would look like: children_age: 0,1,17

- `sort` (string): This parameter orders result by BEST, CHEAPEST or FASTEST flights.

- `cabinClass` (string): Search for flights that match the cabin class specified. Cabin call can be either ECONOMY, PREMIUM_ECONOMY, BUSINESS or FIRST.

- `currency_code` (string): The currency code. currency_code can be retrieved from api/v1/meta/getCurrency(Get Currency) endpoint in Hotels collection.



---


### `search_flight_location`

Find airports by their location, address, state, country, etc.

**端点**: `GET /api/v1/flights/searchDestination`


**参数**:

- `query` (string) *必需*: Names of airport, locations, cities, districts, places, countries, counties etc.

- `languagecode` (string): To obtain the response data in a specific language, enter the languagecode. languagecode can be retrieved from api/v1/meta/getLanguages(Get Languages ) endpoint in Meta collection.



---



## 技术栈

- **FastMCP**: 快速、Pythonic 的 MCP 服务器框架
- **传输协议**: stdio
- **HTTP 客户端**: httpx

## 开发

此服务器由 [API-to-MCP](https://github.com/BACH-AI-Tools/api-to-mcp) 工具自动生成。

版本: 1.0.0
