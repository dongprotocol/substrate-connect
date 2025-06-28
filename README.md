<br /><br />

<div align="center">
   <img height="150" style="object-fit: contain" src="https://i.ibb.co/nMxDdhBW/Substrate-2.jpg" alt="substrate connect">
  <h4 align="center"> Các gói NPM cung cấp một cách tiếp cận sáng tạo để tương tác với các blockchain dựa trên <a href="https://substrate.dev/">Substrate</a>-based trực tiếp trong trình duyệt của bạn.</h4>
</div>

<br /><br />

## Mục lục

- [Mục lục](#table-of-contents)
- [Giới thiệu](#introduction)
  - [Viết dApp An toàn và Hiệu quả với Mạng lưới Polkadot](#write-secure-and-effective-dapps-with-the-polkadot-network)
  - [Tài nguyên Bổ sung](#additional-resources)
  - [Tại sao nên nhúng Light Client vào Tiện ích mở rộng Trình duyệt?](#why-embed-a-light-client-in-browser-extensions)
- [Tài liệu API Toàn diện](#comprehensive-api-documentation)
- [Cấu trúc kho lưu trữ](#repository-structure)
  - [Các Gói](#packages)
  - [Dự án Tiêu biểu](#showcase-projects)
  - [Ví dụ](#examples)
- [Phát triển](#development)
  - [Bắt đầu](#getting-started)
  - [Lệnh Dọn dẹp](#cleanup-commands)
- [Phát hành](#releasing)
- [Liên kết Hữu ích](#useful-links)

## Giới thiệu

Substrate Connect mang đến một phương thức đột phá để tương tác với các blockchain xây dựng trên nền tảng [Substrate](https://substrate.dev/)- trực tiếp trong trình duyệt, loại bỏ nhu cầu sử dụng máy chủ RPC. Bằng cách sử dụng [smoldot](https://github.com/smol-dot/smoldot) - một WASM light client, công cụ này đảm bảo kết nối an toàn và hiệu quả với mạng blockchain mà không phụ thuộc vào các bên trung gian cụ thể.

### Viết các dApp An toàn và Hiệu quả với Mạng lưới Polkadot

Mục tiêu của kho lưu trữ này là cung cấp các gói NPM có thể được sử dụng để:

- **Cung cấp kết nối an toàn và hiệu quả tới mạng lưới Polkadot** thông qua [`@substrate/connect`](./packages/connect/), tận dụng light client WASM xuất sắc là [Smoldot](https://github.com/smol-dot/smoldot).
- **Phát hiện các tiện ích mở rộng trình duyệt** triển khai [giao thức khám phá](./packages/discovery/), bao gồm cả những tiện ích cung cấp light client thông qua [`@substrate/smoldot-discovery`](./packages/smoldot-discovery/). Substrate Connect sẽ tự động tận dụng các tiện ích này khi có thể.
- **Dễ dàng nâng cấp một tiện ích mở rộng trình duyệt** bằng cách tích hợp light client thông qua [`@substrate/light-client-extension-helpers`](./packages/light-client-extension-helpers).

Chúng tôi cũng cung cấp các dự án ví dụ sử dụng các gói trên, bao gồm:

- **[Demo light client cơ bản](./projects/demo)**: một bản demo sử dụng `@substrate/connect` để lấy thông tin về các chuỗi trên mạng Polkadot.
- **[Demo tiện ích mở rộng light client](./projects/extension/)**: một ví dụ về tiện ích trình duyệt cung cấp light client.
- **[Demo tiện ích mở rộng ví](./projects/wallet-template/)**: một ví dụ về tiện ích trình duyệt cung cấp ví Polkadot đầy đủ dựa trên light client.

### Tài nguyên bổ sung

- [Hướng dẫn từng bước](./projects/wallet-template/STEP-BY-STEP-GUIDE.md) cách tích hợp light client vào tiện ích mở rộng trình duyệt.
- Thông tin chi tiết về [Giao thức khám phá](./packages/discovery/), bao gồm cách triển khai trên trình duyệt hoặc tiện ích mở rộng.

### Tại sao nên nhúng Light Client vào Tiện ích Mở rộng Trình duyệt?

Việc tích hợp light client vào tiện ích mở rộng trình duyệt mang lại nhiều lợi ích:

- **Chia sẻ Light Client giữa nhiều dApp:** Nhờ chia sẻ một light client duy nhất giữa nhiều ứng dụng phi tập trung (dApp), thời gian khởi động và đồng bộ hóa được rút ngắn. Điều này giúp các dApp hoạt động mượt mà hơn và nâng cao hiệu quả tổng thể.
- **Vượt qua giới hạn của trình duyệt:** Những hạn chế của trình duyệt đối với WebSocket từ các trang HTTPS gây khó khăn trong việc kết nối nhiều node ngang hàng (peers), do yêu cầu hầu hết các node phải hỗ trợ TLS. Substrate Connect giải quyết vấn đề này bằng cách sử dụng tiện ích mở rộng trình duyệt mạnh mẽ, giúp chuỗi blockchain được đồng bộ ngầm và cải thiện hiệu suất ứng dụng một cách đáng kể. Điều này đảm bảo kết nối ổn định hơn với hệ sinh thái Polkadot.

## Tài liệu API Toàn diện

Để biết cách sử dụng API chi tiết, vui lòng tham khảo [tài liệu API của Substrate Connect](https://paritytech.github.io/substrate-connect).

## Cấu trúc Kho lưu trữ (Repository Structure)

### [Các Gói](./packages/README.md)
   Các triển khai cốt lõi của `@substrate/connect` và `@substrate/discovery`, cùng một số gói hỗ trợ.
   - **[@substrate/discovery](./packages/discovery/)**
   - **[@substrate/connect](./packages/connect/)**
   - **[@substrate/connect-known-chains](./packages/connect-known-chains/)**
   - **[@substrate/connect-discovery](./packages/connect-discovery)** và **[@substrate/smoldot-discovery](./packages/smoldot-discovery/)**

### [Trình diễn Dự án](./projects/)

   Các bản triển khai đầy đủ của `@substrate/connect` và `@substrate/discovery` dành cho ví (Wallet), tiện ích mở rộng (Extension) hoặc mục đích sử dụng chung.

   - **[Triển khai ví](./projects/wallet-template/)**
   - **[Triển khai tiện ích mở rộng](./projects/extension/)**
   - **[Demo parachain](./projects/demo)**


### [Các Ví dụ](./examples/)
   Ví dụ về triển khai `@substrate/connect` và `@substrate/discovery` cho các dApp và tiện ích mở rộng (Extensions).

## Phát triển (Development)

Kho lưu trữ này sử dụng [pnpm workspaces](https://pnpm.io/workspaces) và `corepack`, đảm bảo sử dụng đúng phiên bản pnpm. Nếu bạn muốn đóng góp, vui lòng xem hướng dẫn đóng góp của chúng tôi để hiểu quy trình làm việc và cách tích hợp mượt mà phần đóng góp của bạn vào dự án.

### Bắt đầu (Getting Started)

Làm theo các bước sau để cài đặt mọi thứ và khởi chạy bản demo nếu bạn đang phát triển dự án này:

1. **Cài đặt các yêu cầu** (đã kiểm tra với các phiên bản sau):
   - Node.js (node) v20.9.0
   - pnpm 9.0.6 cài đặt bằng (`npm install -g pnpm`)
   - corepack 0.20.0 (được tích hợp sẵn trong các bản Node.js gần đây)

2. **Sao chép kho lưu trữ**:
   - `git clone https://github.com/paritytech/substrate-connect.git`
   - Đi tới thư mục gốc của dự án root: `cd substrate-connect`

3. **Cài đặt các phụ thuộc**:
   - `corepack pnpm install`

4. **Chạy tiện ích mở rộng ở chế độ phát triển**:
   - Trong terminal A: `cd projects/extension && corepack pnpm dev`

5. **Khởi chạy tiện ích mở rộng**:
   - Trong terminal B: `cd projects/extension && corepack pnpm start`
   - Thao tác này sẽ mở một cửa sổ trình duyệt Chrome với tiện ích đã được tải sẵn. Đảm bảo tiện ích đang hoạt động.

6. **Chạy ứng dụng demo**:
   - Trong terminal C: `cd projects/demo && corepack pnpm dev`
   - Đi tới URL được ghi lại trong trình duyệt Chrome đã mở ở bước 5. Bạn sẽ thấy tiện ích được kích hoạt và ứng dụng demo hiển thị các khối (blocks) mới nhất.

### Lệnh Dọn dẹp (Cleanup Commands)

Xóa tất cả các tệp tạo dựng (build artifacts) trong các workspace của kho lưu trữ:
```bash
corepack pnpm clean
```

Xóa tất cả tệp tạo dựng và cả phụ thuộc (dependencies):
```bash
corepack pnpm deep-clean
```

## Phát hành (Releasing)

Để phát hành phiên bản mới của tiện ích, hãy làm theo các bước được hướng dẫn trong [tài liệu phát hành](./DEPLOY-RELEASE.md).

## Liên kết Hữu ích (Useful Links)

- [Trang tài liệu Substrate Connect](https://substrate.io/developers/substrate-connect/)
- Tải xuống tiện ích từ:
  - [Chrome Store](https://chrome.google.com/webstore/detail/substrate-connect-extensi/khccbhhbocaaklceanjginbdheafklai)
  - [Mozilla Addons](https://addons.mozilla.org/en-US/firefox/addon/substrate-connect/)
