const express = require('express');
const fetch = require('node-fetch'); // Thêm gói này
const app = express();
const port = process.env.PORT || 3000;

const API_URL = 'https://apihitclub.up.railway.app/api/taixiu';

// VIP thuật toán phân tích
function duDoanTaiXiu(ds) {
  const tongList = ds.map(p => p.tong);
  const ketQuaList = tongList.map(t => t >= 11 ? 'Tài' : 'Xỉu');

  const cauTai = ketQuaList.filter(kq => kq === 'Tài').length;
  const cauXiu = ketQuaList.filter(kq => kq === 'Xỉu').length;

  let chuKy = 'Đang theo cầu ';
  if (ketQuaList.slice(-3).every(k => k === 'Tài')) chuKy += 'Tài mạnh';
  else if (ketQuaList.slice(-3).every(k => k === 'Xỉu')) chuKy += 'Xỉu mạnh';
  else chuKy += ketQuaList[ketQuaList.length - 1];

  let duDoan = 'Tài';
  if (cauTai > cauXiu) duDoan = 'Tài';
  else if (cauXiu > cauTai) duDoan = 'Xỉu';
  else duDoan = ketQuaList[ketQuaList.length - 1];

  const doTinCay = Math.round(Math.abs(cauTai - cauXiu) / ds.length * 100);

  return {
    du_doan: duDoan,
    do_tin_cay: `${doTinCay}%`,
    giai_thich: `Phân tích ${ds.length} phiên: ${cauTai} tài - ${cauXiu} xỉu → ${chuKy}`
  };
}

app.get('/api/taixiu', async (req, res) => {
  try {
    const response = await fetch(API_URL);
    const data = await response.json();

    // Dữ liệu từ API bên ngoài
    const phien = data.Phien;
    const ketQua = data.Ket_qua;
    const xuc_xac = data.Xuc_xac;
    const tong = data.Tong;

    // Lưu lịch sử phân tích 10 phiên (giả định API đã tích hợp lịch sử hoặc bạn tự build)
    const lichSu = global.lichSuPhien || [];

    lichSu.push({
      phien: phien,
      ket_qua: ketQua,
      xuc_xac: xuc_xac,
      tong: tong
    });

    if (lichSu.length > 10) lichSu.shift(); // chỉ giữ 10 phiên gần nhất
    global.lichSuPhien = lichSu;

    const logic = duDoanTaiXiu(lichSu);

    const result = {
      ID: "Tele @nhutquangdz",
      Phien: phien,
      Ket_qua: ketQua,
      Xuc_xac: xuc_xac,
      Tong: tong,
      Next_phien: phien + 1,
      Du_doan: logic.du_doan,
      Do_tin_cay: logic.do_tin_cay,
      Giai_thich: logic.giai_thich
    };

    res.json(result);
  } catch (error) {
    res.status(500).json({ error: 'Lỗi khi lấy dữ liệu từ API nguồn.' });
  }
});

app.listen(port, () => {
  console.log(`API VIP Phân tích đang chạy tại cổng ${port}`);
});
