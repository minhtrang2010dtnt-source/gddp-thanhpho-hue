[index.html](https://github.com/user-attachments/files/35266919/index.html)
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Học tập & Đố vui GDĐP Thừa Thiên Huế (10, 11, 12)</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        .bg-hue { background-color: #8B0000; } /* Đỏ Cố đô */
        .text-gold { color: #D4AF37; } /* Vàng Hoàng gia */
        .bg-gold { background-color: #D4AF37; }
    </style>
</head>
<body class="bg-amber-50 min-h-screen text-gray-800 font-sans">
    <!-- Header -->
    <header class="bg-hue text-white shadow-lg p-6 text-center">
        <h1 class="text-3xl font-bold text-gold uppercase tracking-wide">Giáo dục Địa phương tỉnh Thừa Thiên Huế</h1>
        <p class="mt-2 text-amber-200">Hệ thống Trò chơi Đố vui & Tri thức Thiết thực (Khối 10 - 11 - 12)</p>
    </header>

    <!-- Main Content -->
    <main class="max-w-4xl mx-auto my-8 p-6 bg-white rounded-xl shadow-md">
        
        <!-- BỘ LỌC KHỐI LỚP VÀ CHỦ ĐỀ -->
        <div class="mb-6 border-b pb-4 grid grid-cols-1 md:grid-cols-2 gap-4">
            <!-- Chọn Khối Lớp -->
            <div>
                <label class="block font-bold text-gray-700 mb-2">🏫 Chọn Khối lớp:</label>
                <select id="grade-select" onchange="applyFilters()" class="w-full p-2.5 border rounded-lg bg-gray-50 border-gray-300 font-semibold text-gray-700">
                    <option value="all">Tất cả Khối lớp (10, 11, 12)</option>
                    <option value="10">Khối 10</option>
                    <option value="11">Khối 11</option>
                    <option value="12">Khối 12</option>
                </select>
            </div>
            <!-- Chọn Chủ Đề Bài Học -->
            <div>
                <label class="block font-bold text-gray-700 mb-2">📚 Chọn Chủ đề bài học:</label>
                <select id="category-select" onchange="applyFilters()" class="w-full p-2.5 border rounded-lg bg-gray-50 border-gray-300 font-semibold text-gray-700">
                    <option value="all">Tất cả Chủ đề</option>
                    <option value="Lịch sử & Danh thắng">Lịch sử & Danh thắng</option>
                    <option value="Văn học Dân gian">Văn học Dân gian</option>
                    <option value="Âm nhạc & Nghệ thuật">Âm nhạc & Nghệ thuật</option>
                    <option value="Danh nhân Văn hóa">Danh nhân Văn hóa</option>
                    <option value="Di sản & Kiến trúc">Di sản & Kiến trúc</option>
                    <option value="Đô thị Di sản & Công nghệ">Đô thị Di sản & Công nghệ</option>
                </select>
            </div>
        </div>

        <!-- Quiz Container -->
        <div id="quiz-container">
            <div class="flex justify-between items-center border-b pb-4 mb-4">
                <div>
                    <span id="grade-badge" class="bg-red-800 text-gold font-bold px-3 py-1 rounded-full text-sm mr-2">Khối 10</span>
                    <span id="category-badge" class="bg-amber-100 text-amber-900 font-semibold px-3 py-1 rounded-full text-sm">Chủ đề</span>
                </div>
                <span id="score" class="text-lg font-bold text-red-800">Điểm: 0</span>
            </div>

            <!-- Câu hỏi -->
            <h2 id="question" class="text-xl font-bold mb-4 text-gray-900">Nội dung câu hỏi sẽ hiển thị ở đây...</h2>
            
            <!-- KHUNG HÌNH ẢNH MINH HỌA CÂU HỎI -->
            <div id="image-container" class="mb-4 hidden text-center">
                <img id="question-image" src="" alt="Hình ảnh minh họa" class="max-h-64 mx-auto rounded-lg shadow border-2 border-amber-200 object-cover">
            </div>

            <!-- Danh sách đáp án -->
            <div id="options" class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6"></div>

            <!-- Thẻ Giải thích bài học thiết thực -->
            <div id="explanation-box" class="hidden bg-blue-50 border-l-4 border-blue-600 p-4 rounded mb-6">
                <h3 class="font-bold text-blue-900 flex items-center">💡 Thông tin bài học thiết thực:</h3>
                <p id="explanation-text" class="text-blue-800 mt-1 text-sm leading-relaxed"></p>
            </div>

            <button id="next-btn" onclick="nextQuestion()" class="hidden w-full bg-hue hover:bg-red-900 text-gold font-bold py-3 rounded-lg transition duration-200">
                Câu hỏi tiếp theo ➔
            </button>
        </div>
    </main>

    <script>
        // DỮ LIỆU CÂU HỎI CÓ THÊM TRƯỜNG "image" VÀ "category"
        const allQuestions = [
            // KHỐI 10
            {
                grade: "10",
                category: "Lịch sử & Danh thắng",
                question: "Hai thực thể địa lý tự nhiên nào được mệnh danh là biểu tượng gắn bó chặt chẽ và định hình bản sắc Cố đô Huế?",
                image: "[suspicious link removed]", // Ví dụ link ảnh
                options: ["Sông Hương & Núi Ngự", "Sông Bồ & Núi Bạch Mã", "Sông Truồi & Hòn Vượn", "Sông Hương & Đèo Hải Vân"],
                answer: 0,
                explanation: "Sông Hương và núi Ngự Bình là hai biểu tượng tự nhiên - văn hóa tiêu biểu gắn liền với cảnh quan kinh đô xưa."
            },
            {
                grade: "10",
                category: "Văn học Dân gian",
                question: "Thể loại giai thoại dân gian nào ở Huế kể về các nhân vật thuộc dòng dõi hoàng tộc hóm hỉnh, gần gũi với dân dã?",
                image: "", // Không có ảnh thì tự ẩn
                options: ["Giai thoại Hát bội", "Giai thoại Mệ", "Giai thoại Hò Huế", "Vè dân gian"],
                answer: 1,
                explanation: "Giai thoại Mệ là nét đặc trưng riêng có của Huế, phản ánh sự kết hợp cuốn hút giữa tính cách hoàng tộc và sự hóm hỉnh dân dã."
            },

            // KHỐI 11
            {
                grade: "11",
                category: "Âm nhạc & Nghệ thuật",
                question: "Loại hình nghệ thuật âm nhạc nào của Huế đã được UNESCO công nhận là Kiệt tác di sản phi vật thể của nhân loại năm 2003?",
                image: "[suspicious link removed]",
                options: ["Ca Huế trên sông Hương", "Nhã nhạc cung đình Huế", "Hát Chầu văn Huế", "Hát Bài chòi"],
                answer: 1,
                explanation: "Nhã nhạc cung đình Huế là loại hình âm nhạc chính thống triều Nguyễn, đại diện cho đỉnh cao nghệ thuật âm nhạc Việt Nam."
            },
            {
                grade: "11",
                category: "Danh nhân Văn hóa",
                question: "Danh nhân văn hóa, nhà cải cách nổi tiếng nào thời Nguyễn ở Thừa Thiên Huế là người đề xướng tư tưởng đổi mới và làm quan liêm chính?",
                image: "",
                options: ["Tùng Thiện Vương", "Đặng Huy Trứ", "Tuy Lý Vương", "Cao Bá Quát"],
                answer: 1,
                explanation: "Đặng Huy Trứ (làng Thanh Lương, Huế) là nhà canh tân đất nước hàng đầu thế kỷ XIX."
            },

            // KHỐI 12
            {
                grade: "12",
                category: "Di sản & Kiến trúc",
                question: "Loại hình kiến trúc nhà ở truyền thống độc đáo nào ở Huế nổi tiếng với kết cấu khung gỗ kết nối bằng mộng và sân vườn sinh thái?",
                image: "[suspicious link removed]",
                options: ["Nhà ống đô thị", "Nhà Rường - Nhà Vườn Huế", "Nhà sàn vùng cao", "Biệt thự Pháp cổ"],
                answer: 1,
                explanation: "Nhà rường Huế là di sản kiến trúc độc đáo, kết hợp hài hòa giữa không gian sống với thiên nhiên."
            },
            {
                grade: "12",
                category: "Đô thị Di sản & Công nghệ",
                question: "Tỉnh Thừa Thiên Huế hướng tới mục tiêu phát triển thành loại hình đô thị đặc thù nào dưới sự hỗ trợ của công nghệ số (Hue-S)?",
                image: "",
                options: ["Đô thị di sản xanh, sạch, an toàn", "Đô thị công nghiệp nặng", "Trung tâm tài chính thương mại", "Siêu đô thị vệ tinh"],
                answer: 0,
                explanation: "Thừa Thiên Huế hướng tới xây dựng Đô thị di sản trực thuộc Trung ương, phát triển bền vững dựa trên bảo tồn di sản."
            }
        ];

        let activeQuestions = [...allQuestions];
        let currentIdx = 0;
        let score = 0;

        function applyFilters() {
            const selectedGrade = document.getElementById('grade-select').value;
            const selectedCategory = document.getElementById('category-select').value;

            activeQuestions = allQuestions.filter(q => {
                const matchGrade = (selectedGrade === 'all' || q.grade === selectedGrade);
                const matchCategory = (selectedCategory === 'all' || q.category === selectedCategory);
                return matchGrade && matchCategory;
            });

            currentIdx = 0;
            score = 0;
            document.getElementById('score').innerText = `Điểm: ${score}`;
            loadQuestion();
        }

        function loadQuestion() {
            if (activeQuestions.length === 0) {
                document.getElementById('quiz-container').innerHTML = `
                    <div class="text-center py-8">
                        <p class="text-lg text-gray-600 mb-4">Không tìm thấy câu hỏi phù hợp với bộ lọc này!</p>
                        <button onclick="location.reload()" class="bg-hue text-gold px-4 py-2 rounded font-bold">Đặt lại bộ lọc 🔄</button>
                    </div>
                `;
                return;
            }

            const q = activeQuestions[currentIdx];
            document.getElementById('grade-badge').innerText = `Khối ${q.grade}`;
            document.getElementById('category-badge').innerText = q.category;
            document.getElementById('question').innerText = `Câu ${currentIdx + 1}/${activeQuestions.length}: ${q.question}`;
            
            // XỬ LÝ HÌNH ẢNH MINH HỌA
            const imgContainer = document.getElementById('image-container');
            const imgTag = document.getElementById('question-image');
            if (q.image && q.image.trim() !== "") {
                imgTag.src = q.image;
                imgContainer.classList.remove('hidden');
            } else {
                imgContainer.classList.add('hidden');
            }

            document.getElementById('explanation-box').classList.add('hidden');
            document.getElementById('next-btn').classList.add('hidden');
            
            const optionsDiv = document.getElementById('options');
            optionsDiv.innerHTML = '';

            q.options.forEach((opt, idx) => {
                const btn = document.createElement('button');
                btn.className = "w-full text-left p-4 border-2 rounded-lg hover:bg-amber-100 font-medium transition duration-150 border-gray-200";
                btn.innerText = opt;
                btn.onclick = () => selectAnswer(idx, btn);
                optionsDiv.appendChild(btn);
            });
        }

        function selectAnswer(selectedIdx, btn) {
            const q = activeQuestions[currentIdx];
            const buttons = document.getElementById('options').children;
            for (let b of buttons) { b.disabled = true; }

            if (selectedIdx === q.answer) {
                btn.className = "w-full text-left p-4 border-2 rounded-lg bg-green-100 border-green-500 font-bold text-green-900";
                score += 10;
                document.getElementById('score').innerText = `Điểm: ${score}`;
            } else {
                btn.className = "w-full text-left p-4 border-2 rounded-lg bg-red-100 border-red-500 font-bold text-red-900";
                buttons[q.answer].className = "w-full text-left p-4 border-2 rounded-lg bg-green-100 border-green-500 font-bold text-green-900";
            }

            document.getElementById('explanation-text').innerText = q.explanation;
            document.getElementById('explanation-box').classList.remove('hidden');
            document.getElementById('next-btn').classList.remove('hidden');
        }

        function nextQuestion() {
            currentIdx++;
            if (currentIdx < activeQuestions.length) {
                loadQuestion();
            } else {
                document.getElementById('quiz-container').innerHTML = `
                    <div class="text-center py-8">
                        <h2 class="text-3xl font-bold text-hue mb-4">🎉 Hoàn thành Thử thách!</h2>
                        <p class="text-xl mb-6">Tổng điểm của bạn: <span class="font-bold text-red-700">${score}</span> / ${activeQuestions.length * 10}</p>
                        <button onclick="location.reload()" class="bg-hue text-gold px-6 py-3 rounded-lg font-bold hover:bg-red-900">Chơi lại 🔄</button>
                    </div>
                `;
            }
        }

        loadQuestion();
    </script>
</body>
</html>
