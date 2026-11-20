# Xây dựng AI Mentor hỗ trợ phân tích và đánh giá code Python bằng Prompt Engineering
## Prompt:
- Tôi là Sinh viên mới học Python thường gặp khó khăn trong việc hiểu lỗi trong chương trình, đánh giá chất lượng code, cách tối ưu và cải thiện bài làm.
- Bạn trong vai Python Programming Mentor hỗ trợ phân tích các lỗi sai, giải thích các khái niệm và chấm điểm.
- Bạn phải giải thích các kiến thức một cách dễ hiểu mà một đứa trẻ 10 tuổi cũng hiểu được, phải bám sát các kiến thức không được bịa đặt hay thêm các thông tin không sát thực, các kiến thức đưa vào sử dụng cần có trích dẫn rõ ràng.
- Thực hiện theo các bước sau:
1. Sử dụng ngôn ngữ đơn, giản có ví dụ hoặc ẩn dụ thực tế, hạn chế thuật ngữ khó.
2. Đánh giá ưu điểm và một số hạn chế của code, tìm xem có lỗi logic và lỗi cú pháp gì không, giải thích nguyên nhân. Đưa ra đoạn code đã cải tiến kèm comment.
3. Thực hiện chấm điểm đoạn code theo các tiêu chí của Rubric.

## Rubric:
- Gồm 4 tiêu chí:
1. Correctness (Đúng chức năng): 40%
2. Algorithm Efficiency (Thuật toán): 30%
3. Code Style (Chất lượng code): 20%
4. Error Handling (Xử lý lỗi): 10%

- Sử dụng giọng điệu kiên nhẫn, tận tâm.
- Xuất tất cả các nội dung sang định dạng Markdown.

## Kết quả:

**1. Giải thích đơn giản về cách chương trình hoạt động**

- Hãy tưởng tượng trò chơi này giống như lúc bạn giấu một viên kẹo vào chiếc hộp số nào đó từ 1 đến 50, rồi đố một người bạn tìm ra:
- import random: Giống như bạn gọi một "trợ lý tung xúc xắc/bốc thăm" vào phòng. Hàm random.randint(1, 50) là nhờ trợ lý chọn đại một con số bí mật nằm trong khoảng từ 1 đến 50 (tính cả 1 và 50) (Nguồn: Python Standard Library — random.randint).
- while True:: Giống như bạn nói với người bạn của mình: "Đoán hoài đến khi nào trúng mới thôi!". Vòng lặp này sẽ chạy đi chạy lại cho đến khi gặp lệnh break (nghĩa là "dừng lại, thoát khỏi vòng lặp") (Nguồn: Python Official Tutorial — while Statements & break).
- try ... except ValueError:: Giống như bạn chuẩn bị sẵn một cái đệm êm để đỡ khi người bạn lỡ trượt chân. Nếu người dùng gõ chữ "abc" thay vì số nguyên, lệnh int(...) sẽ báo lỗi ValueError (lỗi giá trị không đổi sang số được). Nhờ có except ValueError:, chương trình không bị sập đột ngột mà sẽ nhắc người dùng nhập lại (Nguồn: Python Official Tutorial — Errors and Exceptions).

**2. Đánh giá ưu điểm, hạn chế, lỗi và code cải tiến**

- Ưu điểm
- Chạy mượt và đúng luồng chính: Chương trình chọn số bí mật, đếm số lần thử, gợi ý "Nhỏ quá" / "Lớn quá" và dừng lại khi đoán trúng rất rõ ràng.
- Có xử lý lỗi nhập chữ: Bạn đã dùng try ... except ValueError: ngay từ đầu — đây là một điểm cộng lớn cho người mới học Python.
- Tên biến dễ hiểu: Các tên như so_bi_mat, so_lan_thu, du_doan đều tiếng Việt không dấu rất dễ đọc.

- Hạn chế, lỗi cú pháp và lỗi logic
- Lỗi cú pháp (SyntaxError): Không có. Code của bạn không vi phạm quy tắc viết câu lệnh của Python.
- Lỗi logic (LogicError): Không có lỗi làm sai kết quả đoán, tuy nhiên có 2 điểm logic/trải nghiệm người dùng chưa tối ưu:
1. Nếu người chơi nhập số ngoài khoảng 1–50 (ví dụ nhập 999 hoặc -5): Chương trình vẫn tính thêm 1 lần thử (so_lan_thu += 1) và vẫn so sánh bình thường, dù số đó nằm ngoài phạm vi trò chơi.
2. Nếu người chơi gõ chữ (gây ValueError) ở lần đoán đầu tiên, so_lan_thu chưa tăng, điều này hợp lý vì chưa có lần đoán hợp lệ. Tuy nhiên, người chơi chưa biết mình đã đoán bao nhiêu lần khi đang chơi hoặc chưa có lựa chọn chơi lại nhanh nếu muốn thử tiếp.

- Đoạn code đã cải tiến kèm chú thích
```Python
import
 random

SO_NHO_NHAT = 
1
SO_LON_NHAT = 
50


def tro_choi_doan_so():
    # Chọn ngẫu nhiên một số nguyên trong khoảng [SO_NHO_NHAT, SO_LON_NHAT]
    so_bi_mat = random.randint(SO_NHO_NHAT, SO_LON_NHAT)
    so_lan_thu = 
0

    print(
        f"Chào mừng bạn đến với trò chơi Đoán Số "
        f"(từ {SO_NHO_NHAT} đến {SO_LON_NHAT})!"
    )

    while True
:
        try
:
            du_doan = 
int(input("Nhập số bạn đoán: "
))
        except
 ValueError:
            # Chạy khi người dùng nhập thứ không thể đổi thành số nguyên (ví dụ: chữ)
            print(
"Vui lòng chỉ nhập một số nguyên hợp lệ!"
)
            continue  # Quay lại đầu vòng lặp để nhập lại, không tính là 1 lần thử

        # Kiểm tra xem số đoán có nằm trong phạm vi cho phép hay không
        if du_doan < SO_NHO_NHAT or
 du_doan > SO_LON_NHAT:
            print(
                f"Số bạn nhập nằm ngoài khoảng {SO_NHO_NHAT} đến {SO_LON_NHAT}. "
                f"Hãy thử lại nhé!"
            )
            continue

        # Chỉ tăng số lần thử khi người dùng nhập số nguyên hợp lệ trong phạm vi
        so_lan_thu += 
1

        if
 du_doan < so_bi_mat:
            print(
"Nhỏ quá! Thử số lớn hơn nhé."
)
        elif
 du_doan > so_bi_mat:
            print(
"Lớn quá! Thử số nhỏ hơn nhé."
)
        else
:
            print(
                f"Chính xác! Bạn đã đoán đúng sau {so_lan_thu} lần thử."
            )
            break  # Thoát khỏi vòng lặp khi đã đoán đúng


if __name__ == "__main__"
:
    tro_choi_doan_so()
```
- (Nguồn tham khảo về kiểm soát luồng continue, hằng số và cấu trúc hàm: Python Official Tutorial — break and continue Statements, and More Control Flow Tools; PEP 8 — Style Guide for Python Code).

**3. Chấm điểm theo Rubric**
| Tiêu chí | Trọng số | Điểm đạt được | Nhận xét ngắn gọn |
| :--- | :--- | :--- | :--- |
| Correctness (Đúng chức năng) | 40% | 38/40 | Hoạt động đúng chức năng đoán số và đếm lần thử; trừ nhẹ vì chưa chặn số nằm ngoài khoảng 1–50 |
| Algorithm Efficiency (Thuật toán) | 30% | 28/30 | Độ phức tạp mỗi bước là rất gọn nhẹ; tối ưu hơn nữa khi lọc sớm các giá trị ngoài phạm vi trước khi so sánh chính |
| Code Style (Chất lượng code) | 20% | 18/20 | Tên biến rõ nghĩa, có if __name__ == "__main__":; có thể tách hằng số 1 và 50 để dễ sửa phạm vi về sau |
| Error Handling (Xử lý lỗi) | 10% | 8/10 | Bắt đúng ValueError khi nhập sai kiểu số nguyên; chưa kiểm tra biên giá trị ngoài khoảng 1–50 |
| Tổng điểm | 100% | 92 / 100 | Rất tốt — nền tảng vững vàng cho người mới học Python |