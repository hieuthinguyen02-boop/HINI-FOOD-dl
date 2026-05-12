[donhang6.html](https://github.com/user-attachments/files/27623080/donhang6.html)
# HINI-FOOD-dl<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bảng Đặt Hàng HINI FOOD - Tối Ưu Điện Thoại</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #f0f2f5; padding: 10px; margin: 0; }
        .khung-chinh { max-width: 1000px; margin: auto; background: white; padding: 15px; border-radius: 15px; box-shadow: 0 4px 20px rgba(0,0,0,0.08); }
        h1 { text-align: center; color: #27ae60; font-size: 22px; text-transform: uppercase; border-bottom: 2px solid #27ae60; padding-bottom: 10px; }
        
        /* Khung cuộn ngang cho bảng trên điện thoại */
        .khung-bang { overflow-x: auto; width: 100%; border-radius: 8px; border: 1px solid #ddd; margin-bottom: 20px; }
        table { width: 100%; border-collapse: collapse; min-width: 700px; } /* Đảm bảo bảng không bị bẹp */
        th { background: #27ae60; color: white; padding: 12px; font-size: 14px; position: sticky; top: 0; }
        td { border-bottom: 1px solid #eee; padding: 12px; text-align: center; font-size: 14px; }
        tr:hover { background-color: #f9f9f9; }
        
        .hinh-anh { width: 45px; height: 45px; object-fit: cover; border-radius: 5px; background: #eee; }
        .ten-san-pham { text-align: left; font-weight: bold; color: #2c3e50; min-width: 150px; }
        .o-giam-gia { width: 60px; padding: 5px; border: 1px solid #e74c3c; border-radius: 4px; text-align: center; color: #e74c3c; }
        
        .cum-so-luong { display: flex; justify-content: center; align-items: center; gap: 8px; }
        .nut-bam { width: 32px; height: 32px; cursor: pointer; background: #2ecc71; color: white; border: none; border-radius: 5px; font-size: 18px; font-weight: bold; }
        .so-luong-hien-tai { width: 35px; text-align: center; border: 1px solid #ddd; border-radius: 4px; padding: 5px 0; font-weight: bold; }

        /* Chỉnh lại bố cục thông tin khách trên điện thoại */
        .phan-xac-nhan { display: flex; flex-direction: column; gap: 20px; background: #f8fbff; padding: 20px; border-radius: 12px; border: 1px solid #d6eaf8; }
        @after (min-width: 768px) { .phan-xac-nhan { flex-direction: row; } } /* Máy tính thì nằm ngang */

        .nhap-lieu { flex: 1; }
        .nhap-lieu input, .nhap-lieu textarea { width: 100%; padding: 12px; margin-top: 10px; border: 1px solid #bdc3c7; border-radius: 6px; box-sizing: border-box; font-size: 15px; }
        
        .tong-ket-don { flex: 1; text-align: center; }
        .chu-tong-tien { font-size: 26px; color: #c0392b; font-weight: bold; margin: 15px 0; }
        .nut-gui-don { background: #e67e22; color: white; border: none; padding: 18px; font-size: 18px; border-radius: 10px; cursor: pointer; font-weight: bold; width: 100%; transition: 0.3s; }
        .nut-gui-don:active { transform: scale(0.98); background: #d35400; }
        .nut-gui-don:disabled { background: #bdc3c7; }
        
        #danh-sach-da-chon { text-align: left; background: white; padding: 15px; border-radius: 8px; border: 1px dashed #27ae60; min-height: 50px; font-size: 14px; }
    </style>
</head>
<body>

<div class="khung-chinh">
    <h1>DANH SÁCH ĐẶT HÀNG HINI FOOD</h1>

    <div class="khung-bang">
        <table>
            <thead>
                <tr>
                    <th>STT</th>
                    <th>Ảnh</th>
                    <th>Tên Sản Phẩm</th>
                    <th>Quy Cách</th>
                    <th>Giá Sỉ</th>
                    <th>Giảm Thêm</th>
                    <th>Số Lượng</th>
                    <th>Thành Tiền</th>
                </tr>
            </thead>
            <tbody id="bang-san-pham">
                <script>
                    const sanPhams = [
                        {stt:1, ten:"Chả mực xoắn ống LC", quyCach:"500g", gia:40000},
                        {stt:2, ten:"Chả tôm xoắn ống LC", quyCach:"500g", gia:40000},
                        {stt:3, ten:"Bò cuộn lá lốt LC", quyCach:"500g", gia:47000},
                        {stt:4, ten:"Chả cá sợi BaMi LC", quyCach:"500g", gia:38000},
                        {stt:5, ten:"Chả cá sợi Phú Mark", quyCach:"450g", gia:39000},
                        {stt:6, ten:"Tôm con định hình LC (L1)", quyCach:"500g", gia:45000},
                        {stt:7, ten:"Tôm con định hình Deli (L2)", quyCach:"500g", gia:40000},
                        {stt:8, ten:"Thanh cua Liên Anh", quyCach:"500g", gia:60000},
                        {stt:9, ten:"Thanh cua Phú Mark", quyCach:"450g", gia:47000},
                        {stt:10, ten:"Chả cá Hàn Quốc", quyCach:"450g", gia:29000},
                        {stt:11, ten:"Ốc nhồi hải sản LC", quyCach:"500g", gia:37000},
                        {stt:12, ten:"Chả giò hải sản LC", quyCach:"400g", gia:47000},
                        {stt:13, ten:"Chả giò xốp thịt heo", quyCach:"450g", gia:35000}
                    ];

                    document.write(sanPhams.map(sp => `
                        <tr class="dong-san-pham" data-gia="${sp.gia}">
                            <td>${sp.stt}</td>
                            <td><img src="https://via.placeholder.com/50/27ae60/ffffff?text=Hini" class="hinh-anh"></td>
                            <td class="ten-san-pham">${sp.ten}</td>
                            <td>${sp.quyCach}</td>
                            <td>${sp.gia.toLocaleString()}đ</td>
                            <td><input type="number" value="0" class="o-giam-gia" onchange="tinhToanToanBo()"></td>
                            <td>
                                <div class="cum-so-luong">
                                    <button class="nut-bam" onclick="thayDoiSoLuong(this, -1)">-</button>
                                    <input type="number" value="0" class="so-luong-hien-tai" readonly>
                                    <button class="nut-bam" onclick="thayDoiSoLuong(this, 1)">+</button>
                                </div>
                            </td>
                            <td class="o-thanh-tien">0</td>
                        </tr>
                    `).join(''));
                </script>
            </tbody>
        </table>
    </div>

    <div class="phan-xac-nhan">
        <div class="nhap-lieu">
            <h3>THÔNG TIN KHÁCH HÀNG</h3>
            <input type="text" id="ten-khach" placeholder="Họ và tên người nhận">
            <input type="tel" id="sdt-khach" placeholder="Số điện thoại Zalo">
            <textarea id="dia-chi-khach" rows="3" placeholder="Địa chỉ giao hàng (Số nhà, Tên đường, Phường/Xã...)"></textarea>
        </div>

        <div class="tong-ket-don">
            <h3>ĐƠN HÀNG ĐÃ CHỌN</h3>
            <div id="danh-sach-da-chon">Chưa chọn món nào...</div>
            <div class="chu-tong-tien">TỔNG: <span id="so-tong-tien">0</span>đ</div>
            <button id="nut-gui" class="nut-gui-don" onclick="xacNhanDatHang()">XÁC NHẬN GỬI ĐƠN</button>
        </div>
    </div>
</div>

<script>
    const LINK_GOOGLE_SHEET = "https://script.google.com/macros/s/AKfycbwcrhRglOFF54P7zIybwDP_3SoBLOcx6RtsHlRMIYXpz7AjxaqMW67GBzKfK7EmGdArIw/exec";

    function thayDoiSoLuong(nut, giaTri) {
        const oNhap = nut.parentElement.querySelector('.so-luong-hien-tai');
        let conSoMoi = parseInt(oNhap.value) + giaTri;
        if (conSoMoi < 0) conSoMoi = 0;
        oNhap.value = conSoMoi;
        tinhToanToanBo();
    }

    function tinhToanToanBo() {
        const tatCaDong = document.querySelectorAll('.dong-san-pham');
        let tongTienCuoiCung = 0;
        let vanBanGioHang = "";

        tatCaDong.forEach(dong => {
            const giaGoc = parseInt(dong.getAttribute('data-gia'));
            const giamGia = parseInt(dong.querySelector('.o-giam-gia').value) || 0;
            const soLuong = parseInt(dong.querySelector('.so-luong-hien-tai').value);
            const tenMon = dong.querySelector('.ten-san-pham').innerText;

            const thanhTien = (giaGoc - giamGia) * soLuong;
            dong.querySelector('.o-thanh-tien').innerText = thanhTien.toLocaleString();

            if (soLuong > 0) {
                vanBanGioHang += `• ${tenMon} x${soLuong} = ${thanhTien.toLocaleString()}đ\n`;
                tongTienCuoiCung += thanhTien;
            }
        });

        document.getElementById('so-tong-tien').innerText = tongTienCuoiCung.toLocaleString();
        document.getElementById('danh-sach-da-chon').innerText = vanBanGioHang || "Chưa chọn món nào...";
    }

    async function xacNhanDatHang() {
        const ten = document.getElementById('ten-khach').value.trim();
        const sdt = document.getElementById('sdt-khach').value.trim();
        const diaChi = document.getElementById('dia-chi-khach').value.trim();
        const tongTien = document.getElementById('so-tong-tien').innerText;
        const danhSachMon = document.getElementById('danh-sach-da-chon').innerText;
        const nutGui = document.getElementById('nut-gui');

        if (!ten || !sdt || !diaChi || tongTien === "0") {
            alert("⚠️ Vui lòng nhập đủ thông tin và chọn món!"); return;
        }

        nutGui.disabled = true;
        nutGui.innerText = "⏳ ĐANG GỬI HỆ THỐNG...";

        try {
            await fetch(LINK_GOOGLE_SHEET, {
                method: "POST",
                mode: "no-cors",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({ ten, sdt, diaChi, chiTietMon: danhSachMon, tongTien })
            });
        async function xacNhanDatHang() {
        const ten = document.getElementById('ten-khach').value.trim();
        const sdt = document.getElementById('sdt-khach').value.trim();
        const diaChi = document.getElementById('dia-chi-khach').value.trim();
        const tongTien = document.getElementById('so-tong-tien').innerText;
        const danhSachMon = document.getElementById('danh-sach-da-chon').innerText;
        const nutGui = document.getElementById('nut-gui');

        if (!ten || !sdt || !diaChi || tongTien === "0") {
            alert("⚠️ Vui lòng nhập đủ thông tin và chọn món!"); 
            return;
        }

        nutGui.disabled = true;
        nutGui.innerText = "⏳ ĐANG GỬI HỆ THỐNG...";

        // 1. Gửi dữ liệu ngầm lên Google Sheets
        try {
            await fetch(LINK_GOOGLE_SHEET, {
                method: "POST",
                mode: "no-cors",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({ ten, sdt, diaChi, chiTietMon: danhSachMon, tongTien })
            });
        } catch (e) { 
            console.log("Lỗi gửi Sheets nhưng vẫn tiếp tục mở Zalo"); 
        }

        // 2. Chuẩn bị nội dung tin nhắn Zalo
        // encodeURIComponent giúp chuyển các ký tự xuống dòng, khoảng trắng thành mã mà link web hiểu được
        const noiDungZalo = encodeURIComponent(
            `CHÀO HINI FOOD, TÔI ĐẶT HÀNG:\n` +
            `--------------------------\n` +
            `${danhSachMon}\n` +
            `💰 TỔNG CỘNG: ${tongTien}đ\n` +
            `--------------------------\n` +
            `👤 Khách hàng: ${ten}\n` +
            `📞 SĐT: ${sdt}\n` +
            `📍 Địa chỉ: ${diaChi}`
        );

        // 3. Thông báo và chuyển hướng
        alert("✅ Đơn hàng đã được lưu!\n\nNhấn OK để chuyển sang Zalo gửi tin nhắn chốt đơn cho Shop nhé.");
        
        // Link Zalo cá nhân kèm nội dung soạn sẵn (Lưu ý: Zalo cá nhân đôi khi không tự điền text, 
        // nhưng link này là cách tốt nhất để mở app)
        window.location.href = `https://zalo.me/0908786102`;
        
        // Đặt lại trạng thái nút sau khi khách quay lại
        setTimeout(() => {
            nutGui.disabled = false;
            nutGui.innerText = "XÁC NHẬN GỬI ĐƠN";
        }, 2000);
    }
