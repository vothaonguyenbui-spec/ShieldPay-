<!-- Trang demo cho phép upload và đọc ảnh -->
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Reader Demo</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 40px auto;
            text-align: center;
            padding: 20px;
        }

        h1 {
            color: #333;
        }

        input {
            margin: 20px 0;
        }

        img {
            max-width: 100%;
            max-height: 500px;
            border: 1px solid #ddd;
            border-radius: 8px;
            display: none;
        }

        .info {
            margin-top: 15px;
            color: #555;
        }
    </style>
</head>
<body>

    <h1>Upload và Xem Ảnh</h1>

    <input type="file" id="imageInput" accept="image/*">

    <div class="info" id="fileInfo"></div>

    <br>

    <img id="previewImage">

    <script>
        const imageInput = document.getElementById("imageInput");
        const previewImage = document.getElementById("previewImage");
        const fileInfo = document.getElementById("fileInfo");

        imageInput.addEventListener("change", function() {

            const file = this.files[0];

            if (!file) {
                return;
            }

            fileInfo.innerHTML = `
                <strong>Tên file:</strong> ${file.name}<br>
                <strong>Kích thước:</strong> ${(file.size / 1024).toFixed(2)} KB
            `;

            const reader = new FileReader();

            reader.onload = function(event) {
                previewImage.src = event.target.result;
                previewImage.style.display = "block";
            };

            reader.readAsDataURL(file);
        });
    </script>

</body>
</html>
