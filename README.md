<!DOCTYPE html>
 <html lang="vi">
 <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>Đếm từ</title>
     <style>
         body {
             font-family: Arial, sans-serif;
             margin: 20px;
         }
         textarea {
             width: 100%;
             height: 100px;
         }
         button {
             margin-top: 10px;
         }
         #result {
             margin-top: 20px;
         }
     </style>
 </head>
 <body>
     <h1>Đếm số lần xuất hiện của các từ</h1>
     <textarea id="textInput" placeholder="Nhập đoạn văn bản ở đây..."></textarea>
     <button onclick="countWords()">Đếm từ</button>
     <div id="result"></div>
 
     <script>
         function countWords() {
             const text = document.getElementById('textInput').value;
             const wordsArray = text.toLowerCase().match(/\w+/g);
             const wordCount = {};
 
             if (wordsArray) {
                 wordsArray.forEach(word => {
                     wordCount[word] = (wordCount[word] || 0) + 1;
                 });
             }
 
             displayResults(wordCount);
         }
 
         function displayResults(wordCount) {
             const resultDiv = document.getElementById('result');
             resultDiv.innerHTML = '<h2>Kết quả:</h2>';
             if (Object.keys(wordCount).length === 0) {
                 resultDiv.innerHTML += '<p>Không có từ nào được nhập.</p>';
                 return;
             }
 
             const list = document.createElement('ul');
             for (const [word, count] of Object.entries(wordCount)) {
                 const listItem = document.createElement('li');
                 listItem.textContent = `${word}: ${count}`;
                 list.appendChild(listItem);
             }
             resultDiv.appendChild(list);
         }
     </script>
 </body>
 </html>
