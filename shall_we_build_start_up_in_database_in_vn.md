### Part 2 : Build và bán database ở VN ? Liệu có khả thi.  [WIP]
*Các tiếp cận chưa rõ. chưa phân tích được tổng quan thị trường, chân dung và phân khúc khách hàng. cần phải làm rõ thêm để sharpen ý.* 

Nếu nhìn thị trường Việt Nam: Việc build/startup database from scratch ở VN là điều không thể và cũng không nên. Muốn kiếm tiền thì chắc chỉ có qua 1 vài hướng: 
- Hosted open source database as a service ( manage service ).
- Hoặc packed as a solution để bán ( "chuyển đổi xấu, ơ lộn chuyển đổi số", big data, bi, data warehouse, cdp). 
- Luật VN Data Boundary. Nếu có cái như thế này ra đời thì hoàn toàn có thị phần cho infrastructure  hay database startup. Này là chuyện vĩ mô, dân đen như mình cũng khó biết thực hư, và khi nào. Cái này gọi là thời thế tạo anh hùng. 

Phân thích hướng đầu tiên:

Điều kiện cần:
- Open source trên thế giới đủ ngon, thuận tiện để làm saas. 
- Các anh cloud như FPT, Viettel, VNG bán như add-on service của cloud, cạnh tranh bằng giá, và có thêm Operation support. Nhưng làm sao thì làm cũng phải thật rẻ, bởi vì giá nhân công ở VN rất rẻ, không giống ở Mỹ, thuê 1 DBA, 1 Ops có khi còn đắt hơn mua service. 
- Có technologies advantages : ví dụ giảm 50% chi phí compute and storage.


OLTP trên thế giời đã quá ổn định, và local cloud vendors đều đã bán manage service ở VN. HTAP, CDW thì open sources/market trên thế giới chưa thực sự ổn định, nhưng cũng đang dần shape. Nếu các cloud vendors ở VN muốn đi trước trong mảng này thì có thể adopt 1 số giải pháp open sources và build thành Service rồi bán. Nhưng bán cho ai, bán thế nào mới là thứ cần nghĩ tới trước.  Xét về phân khúc và hành vi người dùng:
- Pure and Large Tech based : phần lớn họ thích tự own, engineering thích tự build hơn là đi buy vì nghĩ mình làm được, và cũng thích làm.  Nếu có mua thì nhu cầu sẽ là từ Product hoặc Marketing đẩy xuống, và mua theo 1 solution package. Bán cho đội này phải thực sự có technologies advantages hoặc abc xyz. Thậm trí có công nghệ ngon, practice xịn họ nghe trình bày giải pháp lên xuống vài vòng rồi về tự build. Nói chung đây là nhóm khách hàng độ khó cấp 4.
- 
- Non tech-based: 
	- Giàu: mua hàng suit vendors như Oracle, Big Query, Snowflake. Không đời nào họ đặt niềm tin vào early startup database, vậy nên " người hãy quên em đi ". Trừ khi bán OLAP db hoặc cloud data warehouse 
	- Trung lưu: nhóm này may ra có cửa, nhưng cái họ cần là fast ROI, thế nên bán pure database có vẻ cũng hơi sai sai.  
	- Nghèo: thường mấy anh outsource cho họ crack db, hoặc dùng open sources. 

 Tất nhiên là sẽ có những ngoại lệ, nhưng nhìn chung muốn startup Db as a service ở VN thì phải build được 2 thứ:
 - Truth and Authority. 
 - Thay đổi tư duy về hành vi của người mua hàng
