## XÀM XÍ DB ĐẦU NĂM 
![visitors](https://visitor-badge.glitch.me/badge?page_id=hungsiro506.blogs.2022_db_trends&left_color=green&right_color=red)


### Part 1 : 2022 database industry reivew:
Trước hết thử nhìn lại thị trường này năm 2022 ở Mẽo có những trendings gì ?

**#1: HTAP hoá mainstream db:**
  
1. Từ năm 2020, Oracle nhận ra rằng AWS kiếm được nhiều tiền hơn họ ( nhiều tỷ $/ năm ) nhờ host Mysql và Postgres qua RDS. Để counter lại, Oracle ra 1 bản extended Mysql với vectorized OLAP engine gọi là Heatwave và cho phép host nó trên cloud của Oracle. Đơn giản hoá lại thì Oracle biến Mysql thành 1 HTAP database vừa phục vụ OLTP, vừa cho phép chạy OLAP query. Một nước đi thực sự hay và tạo trend HTAP hoá những mainstream db trong năm vừa rồi của Oracle. Như mình đã từng nói trước đây, Oracle luôn là trend maker.

2.  Không chỉ Oracle HTAP hoá mà  Snowflake cũng HTAP hoá với Unistore bằng việc support thêm Transactional. 

3. Và Google cho ra AlloyDb, HTAP postgres version với compute và storage tách biệt ( WAL record processing directly in storage). Mấy anh KOL đánh giá AlloyDb là quả boom lớn nhất năm 2022. 

HTAP hoá những mainstream db cực kì hay. Không dễ gì để thay thế 1 OLTP đang chạy ngon lành ở cách doanh nghiệp bằng việc thuyết phục họ chuyển qua 1 giải pháp mới là HTAP. Thế nên việc biến những thứ đã quen thuộc, đã được adopt nhiều như Mysql, Postgres sẽ chiếm ưu thế hơn so việc dụ client mua newly HTAP db như TiDB. Trừ khi build greenfield app ( giống mấy anh ZaloPay ) thì người ta mới liều lĩnh chọn giải pháp mới, vậy nên có thể xem đây như 1 tap-in khá an toàn và hiệu quả. 

**#2 Searching for the next Snowflake in CDW and MPP database.** 

Tiếp nối 2021, nửa đầu năm 2022 có một loạt thương vụ trăm triệu đô gọi vốn:
- Timescale’s [$110m series C](https://www.timescale.com/blog/year-of-the-tiger-110-million-to-build-the-future-of-data-for-developers-worldwide/), 
- Voltron Data’s [$110m seed + series A](https://techcrunch.com/2022/02/17/voltron-data-grabs-110m-to-build-startup-based-on-apache-arrow-project/),
- Dbt Labs’s [$222m series D](https://www.forbes.com/sites/kenrickcai/2022/02/24/dbt-labs-series-d-4-billion-less-than-planned/),
- Starburst announced their [$250m Series D](https://www.starburst.io/blog/starburst-announces-250m-series-d/) in March to expand their Trino offering. 
- Imply  [$100m series D](https://imply.io/blog/imply-raises-100mm-in-series-d-funding/) in May for their commercial version of Druid.
- DataStax got [$115m in funding](https://techcrunch.com/2022/06/15/datastax-proves-its-still-possible-to-raise-nine-figures-at-higher-valuation-in-2022/) on its way to IPO in June. 
- Lastly, SingleStore dropped their [$116m series F](https://www.singlestore.com/media-hub/releases/singlestore-announces-116m-funding) in July and then extended it with another [$30m in October](https://techcrunch.com/2022/10/04/singlestore-raises-30m-more-to-brings-its-database-tech-to-new-customers/).

Và nửa cuối năm thì mọi thứ nguội đi với việc suy thoái chung của tech sector, lạm phát, khủng hoảng. Các anh gọi nhiều như thế trong 2021, 2022 không hiểu sẽ gọi tiếp kiểu gì trong 2023 và 2024 để growth tiếp. Nhưng vấn đề khó hơn là tech sector đang suy thoái, các anh lớn như GG, MS, Amazon, còn phải cắt giảm nhân sự hàng loạt, thì hỏi đại gia nào sẽ chi tiền để mua lại các  start up về Database. Amazon liệu có đi mua lại Clickhouse ( $2B evaluation năm 2021 ) trong khi đã có Redshift và vẫn đang kiếm hàng tỷ đô mỗi năm nhờ nó ? Thế nên các anh db startup này buộc phải 1 trong 2 lựa chọn : IPO or die. Các bác đầu tư vẫn crazy searching for the next Snowflake, nhưng thị trường cũng đang có quá nhiều vendors nên sớm muộn cũng sẽ có kẻ thắng người bại. Mấy anh KOL nói cuối 2025 thì mọi thứ sẽ rõ ràng hơn về OLAP and CDW market. 

P/s: IPO vẫn lỗ. MongoDB vẫn lỗ, Snowflake vẫn lỗ. 

Đoán 2023 sẽ có gì ? [WIP]
