// 1. Tính trừu tượng (Abstraction): Định nghĩa khuôn mẫu cho đối tượng
abstract class SinhVien {
    // 2. Tính đóng gói (Encapsulation): Che giấu dữ liệu bằng private
    private String maSV;
    private String hoTen;

    public SinhVien(String maSV, String hoTen) {
        this.maSV = maSV;
        this.hoTen = hoTen;
    }

    // Getter & Setter để truy cập dữ liệu an toàn
    public String getMaSV() { return maSV; }
    public String getHoTen() { return hoTen; }

    // Phương thức trừu tượng (các lớp con bắt buộc phải cài đặt)
    public abstract void hienThiThongTin();
}

// 3. Tính kế thừa (Inheritance): Lớp SinhVienIT kế thừa từ SinhVien
class SinhVienIT extends SinhVien {
    private double diemJava;

    public SinhVienIT(String maSV, String hoTen, double diemJava) {
        super(maSV, hoTen); // Gọi constructor của lớp cha
        this.diemJava = diemJava;
    }

    // 4. Tính đa hình (Polymorphism): Ghi đè (Override) phương thức của lớp cha
    @Override
    public void hienThiThongTin() {
        System.out.println("[SV IT] Mã: " + getMaSV() + " | Tên: " + getHoTen() + " | Điểm Java: " + diemJava);
    }
}

// Một lớp con khác thể hiện tính đa hình
class SinhVienKinhTe extends SinhVien {
    private double diemMarketing;

    public SinhVienKinhTe(String maSV, String hoTen, double diemMarketing) {
        super(maSV, hoTen);
        this.diemMarketing = diemMarketing;
    }

    @Override
    public void hienThiThongTin() {
        System.out.println("[SV KT] Mã: " + getMaSV() + " | Tên: " + getHoTen() + " | Điểm Marketing: " + diemMarketing);
    }
}

// Lớp chứa hàm main để chạy chương trình
public class Main {
    public static void main(String[] args) {
        // Khởi tạo các đối tượng
        SinhVien sv1 = new SinhVienIT("SV01", "Nguyễn Văn A", 8.5);
        SinhVien sv2 = new SinhVienKinhTe("SV02", "Trần Thị B", 9.0);

        // Gọi phương thức thể hiện tính đa hình
        sv1.hienThiThongTin();
        sv2.hienThiThongTin();
    }
}
