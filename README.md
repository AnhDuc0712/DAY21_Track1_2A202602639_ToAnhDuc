# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Tô Anh Đức
- MSSV / mã học viên: 2A202602639
- Lớp: track 1
- Ngành đã chọn: HR / tuyển dụng

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| Những tác hại chính có thể xảy ra | Hệ thống có thể đánh giá sai mức độ phù hợp của ứng viên với JD, bỏ sót ứng viên tốt hoặc xếp hạng cao ứng viên không phù hợp. AI cũng có thể suy diễn từ CV khi bằng chứng không đầy đủ. Người bị ảnh hưởng chính là ứng viên, HR và phòng ban tuyển dụng. |
| Mức độ high-stakes | **Cao**. Hệ thống hỗ trợ quá trình tuyển dụng, nên kết quả đánh giá có thể ảnh hưởng trực tiếp đến cơ hội việc làm của ứng viên. Vì vậy, AI chỉ nên đóng vai trò hỗ trợ sàng lọc và cung cấp bằng chứng; không được tự động đưa ra quyết định tuyển hoặc loại ứng viên. |
| Dữ liệu nhạy cảm có thể được sử dụng | CV có thể chứa thông tin nhận dạng cá nhân như họ tên, email, số điện thoại, địa chỉ, ảnh, ngày sinh, giới tính, lịch sử học tập và kinh nghiệm làm việc. Trong hệ thống, các thông tin không cần thiết cho việc đánh giá năng lực cần được ẩn hoặc loại bỏ trước khi AI thực hiện matching/ranking. Không sử dụng dữ liệu thật của ứng viên trong bài báo cáo. |
| Nhu cầu human review | **Cao**. HR cần kiểm tra kết quả matching/ranking và bằng chứng mà AI trích xuất trước khi đưa ứng viên sang bước tiếp theo. Phòng ban chuyên môn tiếp tục review các ứng viên được HR chuyển đến và đưa ra đánh giá cuối cùng về chuyên môn. AI không được tự động quyết định tuyển dụng hoặc loại ứng viên. |

### 2. Case study 1 — Amazon AI Recruiting Tool Bias Against Women

#### Brief Case

- Tổ chức / sản phẩm AI: Amazon — công cụ machine learning thử nghiệm dùng để đánh giá và xếp hạng CV ứng viên.

- Thời gian, địa điểm / bối cảnh: Amazon phát triển hệ thống từ khoảng năm 2014; đến năm 2015 công ty phát hiện công cụ không đánh giá ứng viên cho các vị trí kỹ thuật theo cách trung lập về giới. Dự án sau đó bị ngừng. Bối cảnh là hoạt động tuyển dụng nhân sự kỹ thuật tại Amazon.

- AI được dùng để làm gì: Phân tích CV và chấm ứng viên theo thang từ 1 đến 5 sao nhằm hỗ trợ recruiter xác định những ứng viên tiềm năng nhất.

- Vấn đề hoặc sự kiện đáng chú ý: Hệ thống học từ dữ liệu CV lịch sử trong khoảng 10 năm, trong đó phần lớn CV đến từ nam giới. Theo Reuters, mô hình học được xu hướng ưu tiên ứng viên nam, phạt các CV chứa từ “women’s” và hạ điểm ứng viên tốt nghiệp từ một số trường dành cho nữ. Amazon đã thử điều chỉnh hệ thống nhưng cuối cùng không tiếp tục sử dụng công cụ vì không thể bảo đảm mô hình sẽ không tìm ra những tín hiệu khác dẫn đến phân biệt đối xử.

- Số liệu có nguồn: Công cụ sử dụng dữ liệu CV được gửi cho Amazon trong khoảng 10 năm và chấm ứng viên theo thang 1–5 sao. Reuters không cung cấp số lượng ứng viên thực tế bị mất việc hoặc bị loại trực tiếp bởi hệ thống.

- Nguồn: “Amazon scraps secret AI recruiting tool that showed bias against women” — Jeffrey Dastin, Reuters — 10/10/2018. Bản Reuters được lưu/phát lại tại Investing.com và các cơ quan báo chí khác.

- Phân biệt bằng chứng và nhận định: Nguồn xác nhận hệ thống có xu hướng bất lợi với ứng viên nữ, bao gồm việc phạt một số từ liên quan đến phụ nữ và hạ điểm một số trường dành cho nữ. Reuters cũng cho biết recruiter của Amazon có xem các đề xuất của hệ thống nhưng không chỉ dựa duy nhất vào ranking đó. Vì vậy, có bằng chứng rõ về bias trong output của công cụ nhưng chưa đủ bằng chứng để kết luận chính xác bao nhiêu ứng viên nữ thực tế bị từ chối việc làm chỉ vì hệ thống này.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Khi AI phân tích CV và xếp hạng ứng viên trước khi recruiter quyết định ứng viên nào nên được xem xét tiếp cho các vị trí kỹ thuật. |
| Stakeholder bị ảnh hưởng | Ứng viên nữ là stakeholder bị ảnh hưởng trực tiếp; recruiter và Amazon cũng bị ảnh hưởng vì có nguy cơ bỏ qua ứng viên phù hợp và đưa ra quyết định tuyển dụng thiếu công bằng. |
| Failure mode | **Bias / fairness** — mô hình học các pattern từ dữ liệu tuyển dụng lịch sử vốn chủ yếu đến từ nam giới và tạo ra kết quả bất lợi đối với ứng viên nữ. |
| Layer bắt đầu lỗi | **Model / Grounding.** Có bằng chứng rằng mô hình được học từ tập CV lịch sử mất cân bằng giới, nên dữ liệu đầu vào và cách mô hình học từ dữ liệu là nguyên nhân quan trọng. Tuy nhiên, chưa đủ thông tin công khai để xác định chính xác toàn bộ pipeline và lớp kỹ thuật đầu tiên gây lỗi. |
| Harm xảy ra là gì? | Ứng viên nữ có nguy cơ bị đánh giá thấp hoặc mất cơ hội được recruiter xem xét khi CV chứa các tín hiệu mà mô hình liên hệ với giới nữ. Nguồn xác nhận bias trong ranking, nhưng chưa chứng minh được số lượng cụ thể ứng viên mất việc trực tiếp vì công cụ. |
| Harm lens | **Opportunity loss** — mất hoặc giảm cơ hội tiếp cận việc làm; đồng thời có yếu tố **dignity loss** do ứng viên có thể bị đối xử bất lợi dựa trên tín hiệu liên quan đến giới thay vì năng lực. |
| Severity | **High** — ranking tuyển dụng có thể ảnh hưởng trực tiếp đến cơ hội nghề nghiệp của ứng viên, đặc biệt nếu hệ thống được sử dụng ở bước sàng lọc đầu tiên. |
| Scale | **Chưa đủ dữ liệu để đánh giá chính xác.** Công cụ được thiết kế để xử lý nhiều CV cho các vị trí kỹ thuật, nên tiềm năng ảnh hưởng có thể rộng, nhưng nguồn không công bố số ứng viên thực tế bị tác động. |
| Probability | **Medium theo đánh giá của tôi.** Bias đã được quan sát trực tiếp trong output của hệ thống, nhưng recruiter không hoàn toàn tự động làm theo ranking nên không phải mọi output sai đều dẫn tới quyết định tuyển dụng sai. |
| Frequency | **Medium theo đánh giá của tôi.** Nếu công cụ được dùng thường xuyên để xếp hạng CV thì cùng một pattern bias có thể xuất hiện lặp lại; tuy nhiên nguồn không công bố tần suất cụ thể. |
| Vì sao? | Đây là high-risk moment vì AI tham gia trực tiếp vào việc ưu tiên ứng viên trong tuyển dụng. Reuters xác nhận mô hình học từ dữ liệu CV lịch sử phần lớn đến từ nam giới và tạo ra ranking bất lợi với các tín hiệu liên quan tới phụ nữ. Tuy nhiên, recruiter vẫn tham gia quyết định và nguồn không chứng minh hệ thống tự động loại ứng viên, nên tôi đánh giá Severity là High nhưng không đánh Probability hoặc Frequency là High nếu không có thêm dữ liệu. |

### 3. Case study 2 — iTutorGroup Automated Hiring Age Discrimination

#### Brief Case

- Tổ chức / sản phẩm AI: iTutorGroup — phần mềm tuyển dụng trực tuyến dùng để sàng lọc ứng viên tutor tại Hoa Kỳ.

- Thời gian, địa điểm / bối cảnh: Hoa Kỳ, chủ yếu trong giai đoạn tháng 3–4/2020. Vụ việc được EEOC khởi kiện năm 2022 và đạt thỏa thuận dàn xếp năm 2023.

- AI được dùng để làm gì: Phần mềm tự động sàng lọc hồ sơ ứng viên cho các vị trí tutor online.

- Vấn đề hoặc sự kiện đáng chú ý: Theo EEOC, iTutorGroup lập trình phần mềm tuyển dụng để tự động từ chối ứng viên nữ từ 55 tuổi trở lên và ứng viên nam từ 60 tuổi trở lên. Hệ thống đã từ chối hơn 200 ứng viên đủ điều kiện tại Hoa Kỳ dựa trên tuổi.

- Số liệu có nguồn: Hơn **200 ứng viên đủ điều kiện** bị từ chối dựa trên tuổi. iTutorGroup đồng ý trả **365.000 USD** để giải quyết vụ kiện. Thỏa thuận còn yêu cầu các biện pháp chống phân biệt đối xử và EEOC giám sát việc tuân thủ trong ít nhất 5 năm nếu doanh nghiệp tiếp tục hoạt động tuyển dụng tại Hoa Kỳ.

- Nguồn: “iTutorGroup to Pay $365,000 to Settle EEOC Discriminatory Hiring Suit” — U.S. Equal Employment Opportunity Commission — 11/09/2023; “EEOC Sues iTutorGroup for Age Discrimination” — EEOC — 05/05/2022.

- Phân biệt bằng chứng và nhận định: EEOC xác nhận rằng phần mềm được lập trình để tự động loại ứng viên theo ngưỡng tuổi và hơn 200 ứng viên đủ điều kiện bị từ chối. Tuy nhiên, một tài liệu của EEOC lưu ý công nghệ được sử dụng trong case này **không nhất thiết là AI theo nghĩa kỹ thuật**, mà chính xác hơn là một hệ thống automated screening. Vì vậy, case này phù hợp để phân tích rủi ro của automated/algorithmic hiring, nhưng không nên khẳng định đây là mô hình AI machine learning nếu không có bằng chứng thêm.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Khi phần mềm sàng lọc hồ sơ và tự động quyết định ứng viên có được tiếp tục trong quy trình tuyển dụng hay bị loại. |
| Stakeholder bị ảnh hưởng | Ứng viên lớn tuổi là stakeholder bị ảnh hưởng trực tiếp; iTutorGroup và bộ phận tuyển dụng cũng bị ảnh hưởng vì hệ thống tạo ra quyết định tuyển dụng mang tính phân biệt đối xử và dẫn đến rủi ro pháp lý. |
| Failure mode | **Bias / fairness** và **Escalation failure** — hệ thống sử dụng tuổi/giới để tự động loại ứng viên và không chuyển các trường hợp này sang human review trước khi quyết định. |
| Layer bắt đầu lỗi | **Grounding / Safety.** Quy tắc sàng lọc được lập trình để sử dụng tuổi và giới theo cách dẫn tới loại ứng viên. Đồng thời, hệ thống cho phép quyết định tự động được thực thi mà không có bước human review đủ mạnh. Đây không nhất thiết là lỗi của một ML model; EEOC lưu ý hệ thống có thể được xem là automated screening chứ không phải AI theo nghĩa kỹ thuật. |
| Harm xảy ra là gì? | Hơn 200 ứng viên đủ điều kiện bị mất cơ hội việc làm khi hệ thống tự động từ chối họ dựa trên tuổi. Đây là hậu quả đã xảy ra chứ không chỉ là nguy cơ giả định. |
| Harm lens | **Opportunity loss** — ứng viên mất cơ hội việc làm; đồng thời có **dignity loss** vì họ bị đối xử khác biệt dựa trên tuổi và giới thay vì chỉ dựa trên năng lực nghề nghiệp. |
| Severity | **High** — quyết định tự động trực tiếp loại ứng viên khỏi cơ hội việc làm và EEOC xác định hành vi này vi phạm luật chống phân biệt tuổi trong tuyển dụng. |
| Scale | **Medium** — hơn 200 ứng viên đủ điều kiện được xác định là bị ảnh hưởng. Quy mô không phải hàng triệu người nhưng đây là số lượng đáng kể trong một quy trình tuyển dụng cụ thể. |
| Probability | **High trong phạm vi rule bị lỗi** — nếu ứng viên thuộc ngưỡng tuổi đã được lập trình, hệ thống được thiết kế để tự động từ chối họ. Đây không phải xác suất suy đoán ngẫu nhiên mà là hành vi được cài đặt trong rule. |
| Frequency | **High trong giai đoạn hệ thống hoạt động theo rule này** — việc loại ứng viên có thể lặp lại với mỗi hồ sơ thỏa điều kiện tuổi. EEOC ghi nhận hơn 200 trường hợp trong một khoảng thời gian chỉ vài tuần vào năm 2020. |
| Vì sao? | Case này nghiêm trọng hơn case Amazon về bằng chứng hậu quả vì EEOC xác nhận ứng viên thực tế đã bị từ chối. Hệ thống thực hiện quyết định tự động theo thuộc tính tuổi và giới, dẫn đến hơn 200 ứng viên đủ điều kiện mất cơ hội việc làm và thỏa thuận 365.000 USD. Tuy nhiên, cần ghi rõ giới hạn: đây là automated hiring software và không có đủ bằng chứng để gọi chính xác công nghệ bên trong là một mô hình AI/ML. |
