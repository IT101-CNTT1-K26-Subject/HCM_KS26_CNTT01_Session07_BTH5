# Prompt AI đánh giá bài viết theo Rubric

## 1. Prompt đã hiệu chỉnh

> **Cách sử dụng:** Thay `[CHỦ ĐỀ]` bằng chủ đề giảng viên giao và thay `[DÁN BÀI VIẾT CỦA SINH VIÊN]` bằng bài viết cần chấm. Nếu chủ đề chưa được cung cấp, AI phải hỏi lại trước khi chấm, không tự suy đoán chủ đề.

```text
CONTEXT:
Giảng viên giao cho sinh viên viết một bài khoảng 300 từ về chủ đề: [CHỦ ĐỀ]. Giảng viên muốn sử dụng AI để hỗ trợ đánh giá bài viết một cách nhất quán, minh bạch và có căn cứ, thay vì đưa ra nhận xét chung chung.

ROLE:
Bạn là trợ lý chấm bài viết học thuật. Bạn có nhiệm vụ đánh giá bài viết nghiêm túc, công bằng và nhất quán theo đúng Rubric do giảng viên cung cấp. Bạn không được tự nhận mình là giảng viên hoặc khẳng định điểm số là kết quả đánh giá chính thức.

REQUEST:
Thực hiện đầy đủ các yêu cầu trong hai thẻ sau:

<task1>
Chấm bài viết theo 5 tiêu chí và điểm tối đa tương ứng:

| Tiêu chí | Điểm tối đa |
|---|---:|
| Đúng chủ đề | 2.0 |
| Nội dung và lập luận | 3.0 |
| Ví dụ minh họa | 2.0 |
| Cấu trúc bài viết | 1.5 |
| Ngữ pháp và diễn đạt | 1.5 |
| **Tổng điểm** | **10.0** |

Với từng tiêu chí, hãy:
- Nêu điểm đạt được và điểm tối đa.
- Trích dẫn chính xác từ/câu trong bài viết làm minh chứng. Không được tự tạo câu trích dẫn.
- Giải thích minh chứng đó đáp ứng hoặc chưa đáp ứng yêu cầu như thế nào.
- Chỉ rõ điểm mạnh, hạn chế và nguyên nhân bị trừ điểm.
</task1>

<task2>
Tuân thủ các quy định bắt buộc:
1. Giữ nguyên điểm tối đa của từng tiêu chí; không tự ý thay đổi trọng số hoặc thêm tiêu chí tính điểm.
2. Không chấm theo cảm tính. Mọi điểm số phải được giải thích bằng nội dung cụ thể trong bài viết.
3. Không đánh giá cao chỉ vì bài viết dài. Độ dài không tự động làm tăng điểm; chỉ xem xét độ dài khi yêu cầu đề bài có quy định và độ dài ảnh hưởng trực tiếp đến mức độ hoàn thành nhiệm vụ.
4. Không suy diễn ý định của người viết hoặc tự bổ sung luận điểm, ví dụ mà bài viết không có.
5. Phải chỉ rõ lỗi, vị trí hoặc câu có lỗi và đề xuất cách sửa cụ thể.
6. Không trừ điểm hai lần cho cùng một lỗi ở nhiều tiêu chí, trừ khi lỗi đó thực sự ảnh hưởng độc lập đến các tiêu chí khác; nếu có, phải giải thích rõ.
7. Nếu thiếu chủ đề, thiếu bài viết hoặc thiếu thông tin thiết yếu để chấm, hãy hỏi lại. Không tự bịa dữ liệu.
8. Tổng điểm phải được tính bằng phép cộng điểm của 5 tiêu chí và không vượt quá 10.0.
</task2>

EXPLANATION – NGUYÊN TẮC ĐÁNH GIÁ:
- Đúng chủ đề: xem bài có trả lời trực tiếp chủ đề, duy trì trọng tâm và tránh lan man hay không.
- Nội dung và lập luận: xem luận điểm có rõ ràng, hợp lý, được giải thích và liên kết logic hay không.
- Ví dụ minh họa: xem ví dụ có cụ thể, phù hợp và thực sự làm sáng tỏ luận điểm hay chỉ nêu chung chung.
- Cấu trúc bài viết: xem có mở đoạn, triển khai ý và kết đoạn hợp lý; các câu có liên kết hay không.
- Ngữ pháp và diễn đạt: xem lỗi chính tả, dấu câu, ngữ pháp, dùng từ, độ rõ ràng và sự mạch lạc.

Khi cho điểm lẻ, hãy giải thích rõ căn cứ. Có thể dùng mức điểm thập phân đến 0.1 để thể hiện mức độ đáp ứng, nhưng không được dùng con số thay cho lập luận.

ACTIONS – QUY TRÌNH THỰC HIỆN:
1. Đọc toàn bộ đề bài, chủ đề và bài viết của sinh viên.
2. Đánh giá bài viết theo từng tiêu chí trong Rubric.
3. Trích dẫn minh chứng chính xác cho từng điểm số.
4. Xác định điểm mạnh, điểm yếu và các lỗi cụ thể.
5. Đề xuất cách sửa có tính thực hành; khi cần, viết câu sửa mẫu.
6. Cộng điểm của 5 tiêu chí để tính tổng điểm trên thang 10.
7. Kiểm tra lại phép cộng và bảo đảm không thay đổi trọng số.

TONE:
Chuyên nghiệp, nghiêm khắc, khách quan và mang tính hướng dẫn. Không tâng bốc, không nhận xét mơ hồ, không dùng lời lẽ xúc phạm.

EXTRAS – ĐỊNH DẠNG ĐẦU RA:
Trình bày kết quả theo đúng thứ tự:

A. Tóm tắt yêu cầu đề bài
- Chủ đề:
- Độ dài yêu cầu:
- Nhận xét sơ bộ về mức độ đáp ứng đề bài (không cho điểm ở phần này).

B. Bảng Rubric và kết quả chấm
| Tiêu chí | Điểm tối đa | Điểm đạt | Minh chứng trích từ bài | Giải thích chấm điểm |

C. Tổng điểm
- Phép tính: ... + ... + ... + ... + ... = .../10.
- Không quy đổi sang thang điểm khác nếu giảng viên không yêu cầu.

D. Điểm mạnh
- Nêu các điểm mạnh cụ thể, kèm vị trí hoặc câu minh họa.

E. Lỗi và điểm cần cải thiện
| Vị trí/câu trong bài | Vấn đề | Vì sao cần sửa | Đề xuất sửa |

F. Nhận xét tổng kết
- Đánh giá ngắn gọn mức độ đáp ứng yêu cầu.
- Nêu 2–3 việc quan trọng nhất sinh viên nên ưu tiên cải thiện.

G. Gợi ý chỉnh sửa
- Đưa ra một số câu viết lại hoặc hướng phát triển luận điểm.
- Không viết lại toàn bộ bài thay cho sinh viên, trừ khi được yêu cầu.

BÀI VIẾT CẦN CHẤM:
[DÁN BÀI VIẾT CỦA SINH VIÊN]
```

## 2. Ví dụ giả định

### 2.1. Đề bài giả định

**Chủ đề:** Vai trò của việc đọc sách đối với sinh viên.  
**Yêu cầu:** Viết một đoạn/bài ngắn khoảng 300 từ, trình bày quan điểm và sử dụng ví dụ minh họa.

### 2.2. Bài viết giả định của sinh viên

Trong cuộc sống hiện đại, sinh viên tiếp nhận thông tin qua sách, video và mạng xã hội. Theo tôi, đọc sách vẫn quan trọng vì giúp người học mở rộng kiến thức và rèn luyện tư duy. Tuy nhiên, lợi ích ấy chỉ rõ rệt khi sinh viên biết chọn tài liệu phù hợp và vận dụng điều đã đọc.

Trước hết, sách trình bày kiến thức có hệ thống. Khi đọc tài liệu chuyên ngành, sinh viên có thể tìm hiểu một vấn đề từ cơ bản đến nâng cao thay vì chỉ ghi nhớ thông tin ngắn trên Internet. Đọc thường xuyên còn giúp phát triển vốn từ và cách diễn đạt. Qua cách tác giả lựa chọn từ ngữ, sắp xếp câu và giải thích vấn đề, người đọc học được cách trình bày ý tưởng rõ ràng hơn. Kỹ năng này hữu ích khi viết báo cáo hoặc thuyết trình.

Chẳng hạn, sinh viên khó quản lý thời gian có thể đọc sách về phương pháp học tập, rồi thử lập kế hoạch theo tuần. Sau đó, người học theo dõi những nhiệm vụ hoàn thành để điều chỉnh lịch học. Ví dụ này cho thấy kiến thức trong sách có thể gợi ý cách giải quyết vấn đề thực tế. Ngoài ra, khi đọc tác phẩm văn học như *Dế Mèn phiêu lưu ký*, sinh viên có thể suy nghĩ về cách ứng xử và trách nhiệm cá nhân.

Tuy nhiên, không phải tài liệu nào cũng đáng tin cậy hoặc phù hợp. Sinh viên cần tìm hiểu tác giả, nguồn xuất bản và lựa chọn sách theo nhu cầu. Tóm lại, đọc sách giúp sinh viên học tập và phát triển bản thân, nhưng hiệu quả phụ thuộc vào việc lựa chọn, đọc hiểu và vận dụng kiến thức.

### 2.3. Kết quả AI chấm điểm giả định

#### A. Tóm tắt yêu cầu đề bài

- **Chủ đề:** Vai trò của việc đọc sách đối với sinh viên.
- **Độ dài yêu cầu:** Khoảng 300 từ.
- **Nhận xét sơ bộ:** Bài viết bám sát chủ đề, trình bày lợi ích của việc đọc sách, có ví dụ và đề cập điều kiện để việc đọc đạt hiệu quả. Bài có đủ phần mở đầu, triển khai và kết luận. Độ dài không được dùng làm căn cứ cộng điểm riêng.

#### B. Bảng Rubric và kết quả chấm

| Tiêu chí | Điểm tối đa | Điểm đạt | Minh chứng từ bài viết | Giải thích chấm điểm |
|---|---:|---:|---|---|
| Đúng chủ đề | 2.0 | **2.0** | “đọc sách vẫn là một thói quen quan trọng vì nó giúp sinh viên mở rộng kiến thức và rèn luyện khả năng suy nghĩ.” | Nêu trực tiếp vai trò của đọc sách đối với sinh viên và giữ trọng tâm xuyên suốt. Những ý về chọn tài liệu và vận dụng kiến thức vẫn liên quan chủ đề. |
| Nội dung và lập luận | 3.0 | **2.4** | “sách trình bày kiến thức có hệ thống”; “Đọc thường xuyên còn giúp phát triển vốn từ và cách diễn đạt.” | Có hai luận điểm rõ và giải thích được lợi ích. Tuy nhiên, phần giải thích còn khái quát; chưa phân tích sâu giới hạn của sách hoặc cách đánh giá hiệu quả của việc áp dụng kiến thức. |
| Ví dụ minh họa | 2.0 | **1.6** | “sinh viên khó quản lý thời gian có thể đọc sách về phương pháp học tập, rồi thử lập kế hoạch theo tuần.” | Ví dụ quản lý thời gian có tình huống và hành động cụ thể, gắn với luận điểm vận dụng kiến thức. Ví dụ về *Dế Mèn phiêu lưu ký* mới nêu tên tác phẩm và ý nghĩa chung, chưa phân tích chi tiết nội dung để làm sáng tỏ luận điểm. |
| Cấu trúc bài viết | 1.5 | **1.4** | Mở đầu nêu quan điểm; hai đoạn giữa triển khai lợi ích và ví dụ; đoạn cuối bắt đầu bằng “Dù vậy” và kết bằng “Tóm lại”. | Trình tự hợp lý, có chuyển ý và kết luận. Một số ý trong đoạn thân bài có thể được nối kết chặt hơn, đặc biệt giữa ví dụ về kỹ năng quản lý thời gian và ví dụ văn học. |
| Ngữ pháp và diễn đạt | 1.5 | **1.3** | “đọc sách vẫn là một thói quen quan trọng”; “việc đọc thường xuyên”; “đọc sách có vai trò thiết thực” | Câu nhìn chung đúng ngữ pháp và dễ hiểu. Tuy nhiên, từ “đọc” và “sách” lặp lại khá nhiều; một số câu diễn đạt khái quát. Cụm cụm “rồi thử” hơi khẩu ngữ so với văn phong học thuật; có thể thay bằng “sau đó lập”. |
| **Tổng điểm** | **10.0** | **8.7** |  | **2.0 + 2.4 + 1.6 + 1.4 + 1.3 = 8.7/10.** |

#### C. Tổng điểm

**2.0 + 2.4 + 1.6 + 1.4 + 1.3 = 8.7/10.**

Điểm được cộng trực tiếp theo đúng trọng số Rubric. Không cần quy đổi vì tổng điểm tối đa đã là 10.

#### D. Điểm mạnh

1. **Bám sát chủ đề:** Bài viết tập trung vào lợi ích và điều kiện để việc đọc sách có hiệu quả đối với sinh viên.
2. **Có lập luận tương đối rõ:** Hai lợi ích chính là mở rộng kiến thức và cải thiện vốn từ, khả năng diễn đạt được nêu riêng và có giải thích.
3. **Có liên hệ thực tế:** Ví dụ về sinh viên lập kế hoạch học tập cho thấy cách chuyển kiến thức đọc được thành hành động.
4. **Bố cục dễ theo dõi:** Bài có mở đầu, phần triển khai và kết luận; các cụm “Trước hết”, “Bên cạnh đó”, “Dù vậy”, “Tóm lại” giúp định hướng người đọc.

#### E. Lỗi và điểm cần cải thiện

| Vị trí/câu trong bài | Vấn đề | Vì sao cần sửa | Đề xuất sửa |
|---|---|---|---|
| “việc đọc thường xuyên còn giúp người học phát triển vốn từ và khả năng diễn đạt” | Nhận định còn khái quát. | Chưa giải thích rõ việc đọc giúp phát triển vốn từ và diễn đạt bằng cơ chế nào. | Bổ sung: “Khi tiếp xúc với cách dùng từ và cách tổ chức câu trong nhiều văn bản, sinh viên có thể học cách diễn đạt chính xác và đa dạng hơn.” |
| “một sinh viên thường gặp khó khăn khi quản lý thời gian có thể đọc sách về phương pháp học tập...” | Ví dụ có tình huống nhưng thiếu kết quả cụ thể. | Người đọc chưa biết kế hoạch được áp dụng có giúp cải thiện vấn đề hay không. | Bổ sung một kết quả có thể kiểm chứng trong ví dụ giả định, chẳng hạn: “Sau hai tuần, sinh viên so sánh số buổi hoàn thành đúng kế hoạch với tuần trước để đánh giá hiệu quả.” |
| “khi đọc tác phẩm văn học như *Dế Mèn phiêu lưu ký*, sinh viên cũng có thể suy nghĩ về cách ứng xử và trách nhiệm cá nhân.” | Ví dụ văn học chưa được phân tích. | Chỉ nêu tên tác phẩm và kết luận chung, chưa chỉ ra chi tiết nào hỗ trợ luận điểm. | Nêu một tình huống hoặc hành động cụ thể trong tác phẩm rồi giải thích bài học liên quan đến trách nhiệm cá nhân. |
| “rồi thử lập kế hoạch theo tuần” | Cách nối “rồi thử” hơi khẩu ngữ. | Văn phong học thuật nên ưu tiên cách diễn đạt trang trọng và chính xác hơn. | Thay bằng “sau đó lập kế hoạch theo tuần”. |
| Các cụm “đọc sách”, “việc đọc”, “sách” xuất hiện lặp lại. | Lặp từ ở một số câu gần nhau. | Làm diễn đạt kém linh hoạt, dù không gây khó hiểu. | Thay đổi có kiểm soát bằng “hoạt động này”, “quá trình đọc”, “tài liệu” khi đúng nghĩa; tránh thay từ máy móc làm sai ý. |

#### F. Nhận xét tổng kết

Bài viết đáp ứng tốt yêu cầu cơ bản: xác định rõ quan điểm, triển khai các lợi ích của việc đọc sách, đưa ra ví dụ và kết luận phù hợp. Điểm hạn chế chính không nằm ở độ dài mà ở chiều sâu phân tích: một số nhận định chưa được giải thích đầy đủ và ví dụ thứ hai chưa có chi tiết minh họa rõ ràng.

Ba ưu tiên cải thiện:
1. Phân tích sâu hơn mỗi luận điểm thay vì chỉ nêu lợi ích.
2. Phát triển ví dụ bằng tình huống, hành động và kết quả cụ thể.
3. Duy trì văn phong học thuật nhất quán và giảm lặp từ.

#### G. Gợi ý chỉnh sửa

**Câu hiện tại:** “Bên cạnh đó, việc đọc thường xuyên còn giúp người học phát triển vốn từ và khả năng diễn đạt.”

**Gợi ý sửa:** “Bên cạnh việc mở rộng kiến thức, quá trình đọc thường xuyên giúp sinh viên tiếp xúc với cách dùng từ và tổ chức câu đa dạng, từ đó cải thiện khả năng diễn đạt trong báo cáo và thuyết trình.”

**Câu hiện tại:** “Ví dụ này cho thấy đọc sách không chỉ cung cấp thông tin mà còn có thể gợi ý cách giải quyết vấn đề trong thực tế.”

**Gợi ý phát triển:** Sau câu này, người viết có thể bổ sung cách sinh viên theo dõi việc thực hiện kế hoạch và đánh giá kết quả. Như vậy, ví dụ sẽ chứng minh rõ hơn mối liên hệ giữa kiến thức trong sách và thay đổi trong hành động.

---

## 3. Lưu ý khi sử dụng prompt

- Chủ đề trong ví dụ chỉ là giả định. Khi chấm bài thực tế, cần nhập đúng chủ đề và yêu cầu của giảng viên.
- Điểm minh họa **8.7/10** là kết quả giả định để minh họa cách áp dụng Rubric, không phải điểm chuẩn cho các bài viết khác.
- Để tăng tính nhất quán giữa nhiều lần chấm, giảng viên nên cung cấp cùng một đề bài, Rubric và hướng dẫn chấm cho mọi bài viết; bài viết ở trường hợp cần thiết nên được giảng viên rà soát lại.
