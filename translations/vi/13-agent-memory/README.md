# Bộ nhớ cho các tác nhân AI  
[![Agent Memory](../../../translated_images/vi/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Khi thảo luận về những lợi ích độc đáo của việc tạo các tác nhân AI, có hai điểm chính được bàn đến: khả năng gọi công cụ để hoàn thành nhiệm vụ và khả năng cải thiện theo thời gian. Bộ nhớ là nền tảng để tạo ra tác nhân tự cải tiến có thể mang lại trải nghiệm tốt hơn cho người dùng của chúng ta.

Trong bài học này, chúng ta sẽ xem bộ nhớ dành cho các tác nhân AI là gì và cách quản lý, sử dụng nó để mang lại lợi ích cho các ứng dụng của chúng ta.

## Giới thiệu

Bài học này sẽ bao gồm:

• **Hiểu về Bộ nhớ cho tác nhân AI**: Bộ nhớ là gì và tại sao nó lại quan trọng đối với các tác nhân.

• **Triển khai và lưu trữ bộ nhớ**: Các phương pháp thực tiễn để thêm khả năng bộ nhớ cho tác nhân AI của bạn, tập trung vào bộ nhớ ngắn hạn và dài hạn.

• **Làm cho tác nhân AI tự cải tiến**: Cách bộ nhớ cho phép tác nhân học hỏi từ các tương tác trước đó và cải thiện theo thời gian.

## Các triển khai có sẵn

Bài học này bao gồm hai hướng dẫn notebook toàn diện:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Triển khai bộ nhớ sử dụng Mem0 và Azure AI Search với framework Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Triển khai bộ nhớ có cấu trúc sử dụng Cognee, tự động xây dựng đồ thị kiến thức dựa trên embeddings, trực quan hóa đồ thị và truy xuất thông minh

## Mục tiêu học tập

Sau khi hoàn thành bài học này, bạn sẽ biết cách:

• **Phân biệt các loại bộ nhớ khác nhau của tác nhân AI**, bao gồm bộ nhớ làm việc, bộ nhớ ngắn hạn và bộ nhớ dài hạn, cũng như các dạng chuyên biệt như bộ nhớ persona và bộ nhớ theo tập.

• **Triển khai và quản lý bộ nhớ ngắn hạn và dài hạn cho các tác nhân AI** sử dụng framework Semantic Kernel, tận dụng các công cụ như Mem0, Cognee, Whiteboard memory, và tích hợp với Azure AI Search.

• **Hiểu các nguyên lý phía sau tác nhân AI tự cải tiến** và cách hệ thống quản lý bộ nhớ mạnh mẽ đóng góp vào việc học liên tục và thích ứng.

## Hiểu về Bộ nhớ cho tác nhân AI

Về cơ bản, **bộ nhớ cho các tác nhân AI là các cơ chế cho phép họ giữ lại và nhớ lại thông tin**. Thông tin này có thể là các chi tiết cụ thể về một cuộc hội thoại, sở thích người dùng, hành động trước đó hoặc thậm chí các mẫu đã học.

Nếu không có bộ nhớ, các ứng dụng AI thường không trạng thái (stateless), nghĩa là mỗi tương tác bắt đầu lại từ đầu. Điều này dẫn đến trải nghiệm người dùng nhàm chán và gây bực bội khi tác nhân "quên" bối cảnh hoặc sở thích trước đó.

### Tại sao Bộ nhớ lại quan trọng?

Trí thông minh của tác nhân gắn liền sâu sắc với khả năng nhớ và sử dụng thông tin quá khứ. Bộ nhớ cho phép các tác nhân trở nên:

• **Phản ánh**: Học hỏi từ các hành động và kết quả trước đó.

• **Tương tác**: Duy trì bối cảnh trong một cuộc hội thoại đang diễn ra.

• **Chủ động và phản ứng**: Dự đoán nhu cầu hoặc phản hồi phù hợp dựa trên dữ liệu lịch sử.

• **Tự động**: Hoạt động độc lập hơn bằng cách dựa vào kiến thức đã lưu trữ.

Mục tiêu của việc triển khai bộ nhớ là làm cho các tác nhân trở nên **đáng tin cậy và có năng lực hơn**.

### Các loại Bộ nhớ

#### Bộ nhớ làm việc

Hãy nghĩ đây như một mảnh giấy nháp mà tác nhân sử dụng trong một nhiệm vụ hoặc quá trình tư duy đang diễn ra. Nó giữ thông tin ngay lập tức cần thiết để tính bước tiếp theo.

Đối với các tác nhân AI, bộ nhớ làm việc thường nắm bắt những thông tin quan trọng nhất từ một cuộc hội thoại, ngay cả khi lịch sử trò chuyện đầy đủ rất dài hoặc bị cắt ngắn. Nó tập trung vào việc trích xuất những thành phần chính như yêu cầu, đề xuất, quyết định và hành động.

**Ví dụ về Bộ nhớ làm việc**

Trong một tác nhân đặt chuyến đi, bộ nhớ làm việc có thể giữ lại yêu cầu hiện tại của người dùng, ví dụ "Tôi muốn đặt chuyến đi đến Paris". Yêu cầu cụ thể này được giữ trong ngữ cảnh lập tức của tác nhân để hướng dẫn tương tác hiện tại.

#### Bộ nhớ ngắn hạn

Loại bộ nhớ này giữ thông tin trong suốt một cuộc hội thoại hoặc phiên làm việc duy nhất. Nó là bối cảnh của cuộc trò chuyện hiện tại, cho phép tác nhân tham chiếu lại các lượt trước trong đối thoại.

**Ví dụ về Bộ nhớ ngắn hạn**

Nếu người dùng hỏi, "Một chuyến bay đến Paris giá bao nhiêu?" và sau đó tiếp tục hỏi "Còn chỗ ở thì sao?", bộ nhớ ngắn hạn đảm bảo tác nhân hiểu rằng "ở đó" ám chỉ "Paris" trong cùng cuộc hội thoại.

#### Bộ nhớ dài hạn

Đây là thông tin tồn tại qua nhiều cuộc hội thoại hoặc phiên làm việc khác nhau. Nó cho phép tác nhân nhớ sở thích người dùng, các tương tác lịch sử hoặc kiến thức chung trong khoảng thời gian dài. Điều này quan trọng để cá nhân hóa.

**Ví dụ về Bộ nhớ dài hạn**

Một bộ nhớ dài hạn có thể lưu lại rằng "Ben thích trượt tuyết và các hoạt động ngoài trời, thích cà phê với tầm nhìn núi, và muốn tránh các sườn trượt nâng cao vì chấn thương trước đây". Thông tin này, học được từ các tương tác trước, ảnh hưởng đến các đề xuất trong các phiên lập kế hoạch du lịch tương lai, làm cho chúng rất cá nhân hóa.

#### Bộ nhớ Persona

Loại bộ nhớ chuyên biệt này giúp tác nhân phát triển một "cá tính" hoặc "persona" nhất quán. Nó cho phép tác nhân nhớ các chi tiết về bản thân hoặc vai trò dự định, làm cho các tương tác trở nên mềm mại và tập trung hơn.

**Ví dụ về Bộ nhớ Persona**  
Nếu tác nhân du lịch được thiết kế để là một "chuyên gia lập kế hoạch trượt tuyết," bộ nhớ persona có thể củng cố vai trò này, ảnh hưởng đến các phản hồi sao cho phù hợp với giọng điệu và kiến thức của một chuyên gia.

#### Bộ nhớ Quy trình/Theo tập (Workflow/Episodic Memory)

Bộ nhớ này lưu trữ chuỗi các bước mà tác nhân thực hiện trong một nhiệm vụ phức tạp, bao gồm thành công hoặc thất bại. Nó giống như việc nhớ lại các "tập" hoặc trải nghiệm trong quá khứ để học hỏi từ chúng.

**Ví dụ về Bộ nhớ Theo tập**

Nếu tác nhân cố gắng đặt một chuyến bay cụ thể nhưng thất bại do không có sẵn, bộ nhớ theo tập có thể ghi lại thất bại này, giúp tác nhân thử các chuyến bay thay thế hoặc thông báo cho người dùng về vấn đề này một cách thông minh hơn trong lần thử lại tiếp theo.

#### Bộ nhớ Thực thể

Điều này liên quan đến việc trích xuất và ghi nhớ các thực thể cụ thể (như người, địa điểm hoặc vật thể) và các sự kiện từ cuộc trò chuyện. Nó cho phép tác nhân xây dựng một hiểu biết có cấu trúc về các yếu tố chính được thảo luận.

**Ví dụ về Bộ nhớ Thực thể**

Từ cuộc trò chuyện về một chuyến đi trước, tác nhân có thể trích xuất "Paris," "Tháp Eiffel," và "bữa tối tại nhà hàng Le Chat Noir" như các thực thể. Trong tương tác tương lai, tác nhân có thể nhớ "Le Chat Noir" và đề nghị đặt một chỗ mới ở đó.

#### Structured RAG (Truy xuất Tăng cường có Cấu trúc)

Mặc dù RAG là một kỹ thuật rộng hơn, "Structured RAG" được nhấn mạnh như một công nghệ bộ nhớ mạnh mẽ. Nó trích xuất thông tin đặc, có cấu trúc từ nhiều nguồn khác nhau (cuộc trò chuyện, email, hình ảnh) và sử dụng chúng để nâng cao độ chính xác, khả năng nhớ và tốc độ phản hồi. Khác với RAG cổ điển dựa chỉ vào sự tương đồng ngữ nghĩa, Structured RAG làm việc với cấu trúc vốn có của thông tin.

**Ví dụ về Structured RAG**

Thay vì chỉ khớp từ khóa, Structured RAG có thể phân tích chi tiết chuyến bay (điểm đến, ngày, giờ, hãng bay) từ một email và lưu chúng theo cách có cấu trúc. Điều này cho phép truy vấn chính xác như "Tôi đã đặt chuyến bay nào đến Paris vào thứ Ba?"

## Triển khai và Lưu trữ Bộ nhớ

Triển khai bộ nhớ cho các tác nhân AI bao gồm một quy trình hệ thống gọi là **quản lý bộ nhớ**, bao gồm tạo, lưu trữ, truy xuất, tích hợp, cập nhật, và thậm chí "quên" (hoặc xóa) thông tin. Việc truy xuất là một khía cạnh đặc biệt quan trọng.

### Công cụ Bộ nhớ chuyên biệt

#### Mem0

Một cách để lưu trữ và quản lý bộ nhớ tác nhân là sử dụng các công cụ chuyên biệt như Mem0. Mem0 hoạt động như một lớp bộ nhớ liên tục, cho phép các tác nhân nhớ lại các tương tác liên quan, lưu sở thích người dùng cùng bối cảnh sự thật, và học từ các thành công, thất bại theo thời gian. Ý tưởng ở đây là các tác nhân không trạng thái trở thành tác nhân có trạng thái.

Nó hoạt động qua **quy trình bộ nhớ hai giai đoạn: trích xuất và cập nhật**. Đầu tiên, các tin nhắn được thêm vào luồng của tác nhân được gửi đến dịch vụ Mem0, sử dụng Mô hình Ngôn ngữ Lớn (LLM) để tóm tắt lịch sử cuộc trò chuyện và trích xuất các ký ức mới. Sau đó, một giai đoạn cập nhật do LLM điều khiển xác định có nên thêm, sửa đổi hoặc xóa những ký ức này hay không, lưu trữ chúng trong một kho dữ liệu lai có thể bao gồm cơ sở dữ liệu vector, đồ thị và key-value. Hệ thống này cũng hỗ trợ nhiều loại bộ nhớ khác nhau và có thể tích hợp bộ nhớ đồ thị để quản lý quan hệ giữa các thực thể.

#### Cognee

Một phương pháp mạnh mẽ khác là sử dụng **Cognee**, một bộ nhớ ngữ nghĩa mã nguồn mở cho tác nhân AI chuyển đổi dữ liệu có cấu trúc và phi cấu trúc thành các đồ thị tri thức có thể truy vấn, được hỗ trợ bởi embeddings. Cognee cung cấp **kiến trúc lưu trữ kép** kết hợp tìm kiếm tương đồng vector với các quan hệ đồ thị, giúp các tác nhân hiểu không chỉ thông tin nào giống nhau, mà còn các khái niệm liên quan với nhau ra sao.

Nó xuất sắc trong **truy xuất lai** kết hợp sự tương đồng vector, cấu trúc đồ thị và lập luận LLM - từ tìm kiếm các đoạn dữ liệu thô đến trả lời câu hỏi có ý thức về đồ thị. Hệ thống duy trì **bộ nhớ sống động**, tiến hóa và tăng trưởng trong khi vẫn có thể truy vấn như một đồ thị kết nối duy nhất, hỗ trợ cả bối cảnh phiên ngắn hạn và bộ nhớ dài hạn liên tục.

Hướng dẫn notebook Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) minh họa xây dựng lớp bộ nhớ thống nhất này, với các ví dụ thực tế về nhập khẩu dữ liệu đa dạng, trực quan hóa đồ thị tri thức, và truy vấn với các chiến lược tìm kiếm khác nhau phù hợp với nhu cầu cụ thể của tác nhân.

### Lưu trữ Bộ nhớ với RAG

Ngoài các công cụ bộ nhớ chuyên biệt như mem0, bạn có thể tận dụng các dịch vụ tìm kiếm mạnh mẽ như **Azure AI Search làm backend để lưu trữ và truy xuất bộ nhớ**, đặc biệt cho Structured RAG.

Điều này cho phép bạn căn cứ phản hồi của tác nhân với dữ liệu của riêng bạn, đảm bảo câu trả lời phù hợp và chính xác hơn. Azure AI Search có thể được dùng để lưu trữ bộ nhớ du lịch cụ thể của người dùng, danh mục sản phẩm, hoặc bất kỳ kiến thức chuyên ngành nào khác.

Azure AI Search hỗ trợ các khả năng như **Structured RAG**, rất mạnh trong việc trích xuất và truy xuất thông tin đặc, có cấu trúc từ các tập dữ liệu lớn như lịch sử cuộc trò chuyện, email, hoặc thậm chí hình ảnh. Điều này cung cấp "độ chính xác và khả năng nhớ siêu phàm" so với các phương pháp chia nhỏ văn bản và embeddings truyền thống.

## Làm cho các tác nhân AI tự cải tiến

Một mô hình phổ biến để các tác nhân tự cải tiến là giới thiệu một **"tác nhân tri thức"**. Tác nhân riêng biệt này quan sát cuộc trò chuyện chính giữa người dùng và tác nhân chính. Vai trò của nó là:

1. **Xác định thông tin có giá trị**: Đánh giá xem phần nào của cuộc hội thoại xứng đáng lưu lại dưới dạng kiến thức chung hoặc sở thích người dùng cụ thể.

2. **Trích xuất và tóm tắt**: Chắt lọc những học hỏi hoặc sở thích thiết yếu từ cuộc hội thoại.

3. **Lưu trữ trong cơ sở tri thức**: Giữ thông tin đã trích xuất, thường trong cơ sở dữ liệu vector, để có thể truy xuất sau này.

4. **Tăng cường truy vấn tương lai**: Khi người dùng bắt đầu truy vấn mới, tác nhân tri thức lấy thông tin liên quan đã lưu và thêm vào prompt của người dùng, cung cấp bối cảnh quan trọng cho tác nhân chính (tương tự như RAG).

### Tối ưu hóa cho Bộ nhớ

• **Quản lý độ trễ**: Để tránh làm chậm tương tác người dùng, một mô hình nhẹ, nhanh hơn có thể được sử dụng đầu tiên để nhanh chóng kiểm tra xem thông tin có đáng lưu hay truy xuất không, chỉ gọi quy trình trích xuất/truy xuất phức tạp hơn khi cần.

• **Bảo trì cơ sở tri thức**: Đối với cơ sở tri thức ngày càng lớn, thông tin ít được sử dụng có thể được di chuyển vào "lưu trữ lạnh" để quản lý chi phí.

## Còn thắc mắc về bộ nhớ của tác nhân?

Tham gia [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) để gặp gỡ các học viên khác, tham dự giờ làm việc và nhận câu trả lời cho các câu hỏi về tác nhân AI của bạn.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Tuyên bố miễn trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, vui lòng lưu ý rằng bản dịch tự động có thể chứa các lỗi hoặc sự không chính xác. Tài liệu gốc bằng ngôn ngữ mẹ đẻ của nó nên được xem là nguồn thông tin chính xác và đáng tin cậy. Đối với các thông tin quan trọng, nên sử dụng dịch thuật chuyên nghiệp bởi con người. Chúng tôi không chịu trách nhiệm về bất kỳ sự hiểu lầm hoặc giải thích sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->