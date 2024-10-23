# React Questions & Answers (বাংলা)

| SN | প্রশ্ন |
|----|--------|
| 1  | **Q: React-এর ডিক্লারেটিভ এপ্রোচ কীভাবে কাজ করে?** <br><br> React-এ প্রতিটি কম্পোনেন্ট তার বর্তমান `state` এবং `props` অনুযায়ী UI কেমন হবে তা ডিক্লারেটিভভাবে ঘোষণা করে। যখন `state` বা `props` পরিবর্তিত হয়, React স্বয়ংক্রিয়ভাবে DOM-কে সেই অনুযায়ী আপডেট করে এবং শুধু প্রয়োজনীয় অংশগুলো efficiently পুনরায় রেন্ডার করে। <br><br>|
| 2  | **Q: কেন props মিরর করা এড়িয়ে চলা উচিত?** <br><br> Don't mirror props in state (প্রপ্স মিরর করা এড়িয়ে চলতে হবে) বলতে বোঝায়, React কম্পোনেন্টে সরাসরি props এর মান state-এ কপি বা mirror না করা। এর কারণ হলো, props এবং state আলাদা কাজ করে। <br> ১। Props হচ্ছে parent কম্পোনেন্ট থেকে পাঠানো ডেটা যা child কম্পোনেন্টে immutable (পরিবর্তনযোগ্য নয়) হিসেবে কাজ করে। <br> ২। State হচ্ছে কম্পোনেন্টের অভ্যন্তরীণ mutable ডেটা, যা কম্পোনেন্টের মধ্যে পরিবর্তন হতে পারে। <br><br>|
| 3  | **Q: কেন props মিরর করলে সমস্যা হতে পারে?** <br><br> ১। প্রথমবার প্রপ্স মিরর: যখন আপনি প্রথমে props থেকে state সেট করেন, চাইল্ড কম্পোনেন্ট props অনুযায়ী কাজ করে। <br> ২। State আপডেট হয় কিন্তু প্রপ্স নয়: চাইল্ডে যদি state কোনো কারণে আপডেট হয় (যেমন, ইউজার ইন্টার‌্যাকশন বা ইভেন্টের মাধ্যমে), React সেই আপডেটেড state-টাই মনে রাখে। <br> ৩। প্যারেন্টের props পরিবর্তন: পরবর্তীতে যদি প্যারেন্ট থেকে নতুন props আসে, চাইল্ডের state আপডেট না হয় কারণ state পরিবর্তন হওয়ার কোনো ইভেন্ট ঘটেনি। React মনে করে state এখনও সঠিক এবং সেই কারণে চাইল্ডে নতুন props প্রতিফলিত হয় না। <br><br>|
| 4  | **Q: মূল পয়েন্টগুলো কেন props মিরর করা উচিত নয়?** <br><br> ১। প্রথমবার প্রপ্স চাইল্ডে সঠিকভাবে কাজ করে। <br> ২। চাইল্ডের state আপডেট হলে React সেটাই মনে রাখে এবং state অনুযায়ী কাজ করে। <br> ৩। প্যারেন্ট থেকে প্রপ্স পরিবর্তিত হলেও চাইল্ড কম্পোনেন্ট সেই নতুন প্রপ্স নেয় না, কারণ React আগের state ধরে রাখে। <br> ৪। এই কারণেই প্রপ্স মিরর করা উচিত নয়, কারণ এটি ডেটা sync-এর সমস্যা তৈরি করে এবং UI সঠিকভাবে আপডেট হয় না। <br><br>|
