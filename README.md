<!DOCTYPE html><html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>মাইক্রোজব সাইট</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; }
        .container { max-width: 600px; margin: auto; padding: 20px; }
        .job, .profile, .admin-panel { border: 1px solid #ddd; padding: 10px; margin: 10px; border-radius: 5px; }
        button { background: green; color: white; padding: 10px; border: none; cursor: pointer; }
        .post-job, .payment, .review, .profile, .admin-panel { margin-top: 20px; padding: 15px; border: 1px solid #ddd; border-radius: 5px; }
        input, textarea { width: 100%; padding: 10px; margin: 5px 0; border: 1px solid #ccc; border-radius: 5px; }
    </style>
</head>
<body>
    <div class="container">
        <h1>মাইক্রোজব সাইট</h1>
        <p>ছোট ছোট কাজ পোস্ট করুন এবং গ্রহণ করুন</p><div class="profile">
        <h2>ইউজার প্রোফাইল</h2>
        <input type="text" placeholder="আপনার নাম" id="userName">
        <input type="email" placeholder="আপনার ইমেইল" id="userEmail">
        <button onclick="saveProfile()">প্রোফাইল সংরক্ষণ করুন</button>
        <p id="profileInfo"></p>
    </div>
    
    <div class="post-job">
        <h2>কাজ পোস্ট করুন</h2>
        <input type="text" placeholder="কাজের শিরোনাম" id="jobTitle">
        <textarea placeholder="কাজের বিবরণ" id="jobDescription"></textarea>
        <input type="number" placeholder="মূল্য (টাকা)" id="jobPrice">
        <button onclick="postJob()">পোস্ট করুন</button>
    </div>
    
    <div id="jobList">
        <div class="job">
            <h3>ডাটা এন্ট্রি কাজ</h3>
            <p>মূল্য: ২০০ টাকা</p>
            <button onclick="makePayment(200)">কাজ গ্রহণ করুন</button>
        </div>
        
        <div class="job">
            <h3>লোগো ডিজাইন</h3>
            <p>মূল্য: ৫০০ টাকা</p>
            <button onclick="makePayment(500)">কাজ গ্রহণ করুন</button>
        </div>
    </div>
    
    <div class="payment">
        <h2>পেমেন্ট সিস্টেম</h2>
        <p>বিকাশ / নগদ / রকেট মাধ্যমে পেমেন্ট করুন</p>
        <input type="number" placeholder="পেমেন্ট অ্যামাউন্ট" id="paymentAmount">
        <button onclick="confirmPayment()">পেমেন্ট করুন</button>
    </div>
    
    <div class="review">
        <h2>রিভিউ দিন</h2>
        <textarea placeholder="আপনার মতামত লিখুন" id="reviewText"></textarea>
        <button onclick="submitReview()">জমা দিন</button>
    </div>
    
    <div class="admin-panel">
        <h2>অ্যাডমিন প্যানেল</h2>
        <p>এখানে এডমিন কাজগুলো ম্যানেজ করতে পারবেন</p>
        <button onclick="showJobs()">সকল কাজ দেখুন</button>
        <button onclick="clearJobs()">সব কাজ মুছুন</button>
    </div>
</div>

<script>
    function saveProfile() {
        var name = document.getElementById("userName").value;
        var email = document.getElementById("userEmail").value;
        if (name && email) {
            document.getElementById("profileInfo").innerHTML = `প্রোফাইল: ${name} (${email})`;
            alert("প্রোফাইল সংরক্ষণ করা হয়েছে!");
        } else {
            alert("অনুগ্রহ করে নাম ও ইমেইল লিখুন!");
        }
    }
    
    function postJob() {
        var title = document.getElementById("jobTitle").value;
        var description = document.getElementById("jobDescription").value;
        var price = document.getElementById("jobPrice").value;
        
        if (title && description && price) {
            var jobList = document.getElementById("jobList");
            var jobDiv = document.createElement("div");
            jobDiv.classList.add("job");
            jobDiv.innerHTML = `<h3>${title}</h3><p>${description}</p><p>মূল্য: ${price} টাকা</p><button onclick="makePayment(${price})">কাজ গ্রহণ করুন</button>`;
            jobList.appendChild(jobDiv);
        } else {
            alert("অনুগ্রহ করে সব তথ্য দিন!");
        }
    }

    function makePayment(amount) {
        document.getElementById("paymentAmount").value = amount;
        alert(`আপনি ${amount} টাকা পেমেন্ট করতে যাচ্ছেন`);
    }
    
    function confirmPayment() {
        var amount = document.getElementById("paymentAmount").value;
        if (amount) {
            alert(`আপনার ${amount} টাকা পেমেন্ট সফল হয়েছে!`);
        } else {
            alert("অনুগ্রহ করে একটি বৈধ পরিমাণ লিখুন!");
        }
    }
    
    function submitReview() {
        var review = document.getElementById("reviewText").value;
        if (review) {
            alert("ধন্যবাদ! আপনার রিভিউ জমা হয়েছে।");
        } else {
            alert("অনুগ্রহ করে একটি রিভিউ লিখুন!");
        }
    }
    
    function showJobs() {
        alert("সকল কাজ দেখানো হবে (এই ফিচার আপগ্রেড করতে হবে)");
    }
    
    function clearJobs() {
        document.getElementById("jobList").innerHTML = "";
        alert("সব কাজ মুছে ফেলা হয়েছে!");
    }
</script>

</body>
</html>
