# X-MASCTF-Write-up
<!-- wp:paragraph -->
<p>Bài write-up đầu tiên của mình về CTF. Xem như là first blood  !O-O<br>Dù là mình đang tập chơi pwn nhưng ở giải này mình lại không giải được bài pwn nào hết.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>Misc - Santa The Weaver </h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Bài này đề cho 1 file zip. Giải nén ra thì mình được file flag.png . Vì là Misc nên mình thử ngay lệnh <strong>strings</strong></p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":34,"align":"center"} -->
<div class="wp-block-image"><figure class="aligncenter"><img src="https://lr04d.files.wordpress.com/2018/12/image-2.png" alt="" class="wp-image-34"/></figure></div>
<!-- /wp:image -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted">Flag: X-MAS{S4n7a_l1k3s_h1di()g_gif7$}</pre>
<!-- /wp:preformatted -->

<!-- wp:heading {"level":3} -->
<h3>Reverse - Endless Christmas</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Đề cho 1 file thực thi. Đầu tiên mình cho vào ida nhưng lại không thấy chỗ nào đặc biệt cả. Sau đó mình chạy file này thì nó lại chạy ra nhiều file khác. Thử bỏ vào ida các file này. Đầu tiên không có gì đặc biệt cho đến khi check file cuối cùng thì</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":36} -->
<figure class="wp-block-image"><img src="https://lr04d.files.wordpress.com/2018/12/image-3.png" alt="" class="wp-image-36"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Đoạn này thì cho 1 đoạn ký tự rồi xor nó với 0xD. Tới đây thì code lại thôi:<br></p>
<!-- /wp:paragraph -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted">s = "U @L^vi&gt;n=i&gt;R9;9&lt;cR9ciR9;9&lt;cR9ciR9;9&lt;cR9ciR9;9&lt;cR9ciRka9;p"<br> flag=''<br> for i in range(len(s)):<br>     x = chr(ord(s[i]) ^ 0xD)<br>     flag += x;<br> print (flag) </pre>
<!-- /wp:preformatted -->

<!-- wp:paragraph -->
<p>Và ra flag: X-MAS{d3c0d3_4641n_4nd_4641n_4nd_4641n_4nd_4641n_4nd_fl46}</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>Web - Santa's lucky number</h3>
<!-- /wp:heading -->

<!-- wp:image {"id":37,"align":"center"} -->
<div class="wp-block-image"><figure class="aligncenter"><img src="https://lr04d.files.wordpress.com/2018/12/image-4.png" alt="" class="wp-image-37"/></figure></div>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Đề cho mình 3 page. Mình thử nhấn vào đó thì nó ra chuỗi ký tự. Đầu tiên mình thử decode nhưng nó không ra gì cả. Sau đó chú ý đến đoạn url của nó : <strong>http://199.247.6.180:12005/?page=1&nbsp;</strong><br>Mình thử thay thành <strong>http://199.247.6.180:12005/?page=flag</strong> web chỉ thay đổi thành chuỗi ban đầu thành chuỗi khác. Suy nghĩ một hồi, mình nghĩ nó chắc ẩn flag đâu đó trong là 1 dãy số nên mình quyết định bruce force xem thế nào. Vì lần đầu code cái này nên mình chỉ nghỉ nó đơn giản thôi.</p>
<!-- /wp:paragraph -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted">import os<br> for i in range(0,1000):<br>     s = "curl http://199.247.6.180:12005/?page="<br>     s += str(i)<br>     os.system(s)</pre>
<!-- /wp:preformatted -->

<!-- wp:paragraph -->
<p>Đầu tiên mình thử chạy nó từ 0 - 1000 nhưng không ra gì. Có khi nào sai không nhỉ? Thử lại thêm lần nữa, lần này là từ 1000 - 2000, lần này thì may mắn đã mỉm cười với mình</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":38,"align":"center"} -->
<div class="wp-block-image"><figure class="aligncenter"><img src="https://lr04d.files.wordpress.com/2018/12/image-5.png" alt="" class="wp-image-38"/></figure></div>
<!-- /wp:image -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted"> Flag: X-MAS{W00pS_S0m30n3_73l1_S4n7a_h1s_c00k1eS_Ar3_BuRn1ng} </pre>
<!-- /wp:preformatted -->

<!-- wp:heading {"level":3} -->
<h3>Forensics - Oh Christmas Tree</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Bài này thì cho 1 file ảnh. Đầu tiên mình thử ngay <strong>strings </strong>nhưng lần này may mắn không mỉm cười nữa rồi. Mình chỉ được 1 đoạn của flag</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":40,"align":"center"} -->
<div class="wp-block-image"><figure class="aligncenter"><img src="https://lr04d.files.wordpress.com/2018/12/image-7.png" alt="" class="wp-image-40"/></figure></div>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Không ra được flag nên mình thử xem hex nó ra sao. Lần này thì may mắn hơn, flag đã ra nhưng nó lại bị tách rời, thôi thì ngồi ghép flag lại vậy. </p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":41,"align":"center"} -->
<div class="wp-block-image"><figure class="aligncenter"><img src="https://lr04d.files.wordpress.com/2018/12/image-8.png" alt="" class="wp-image-41"/></figure></div>
<!-- /wp:image -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted">Flag: X-MAS{0_Chr15tmas_tr33_1s_th1s_a_flag_i_wond3r}<br></pre>
<!-- /wp:preformatted -->

<!-- wp:heading {"level":3} -->
<h3>Forensics - Message from Santa</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Từ đề bài mình nhận được 1 file .img. Đầu tiên mình thử mở nó ra xem nhưng bị lỗi. Check binwalk thì mình thấy nó chứa khá nhiều file ảnh. Loay hoay 1 hồi trên mạng thì mình tìm được 1 tool đó là foremost. Chạy foremost mình thu được 1 folder hình bị cắt ra.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":42} -->
<figure class="wp-block-image"><img src="https://lr04d.files.wordpress.com/2018/12/image-9.png" alt="" class="wp-image-42"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Đến đây thì có flag rồi, ngồi ghép lại thôi</p>
<!-- /wp:paragraph -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted">Flag: X-MAS{1t_l00k5_l1k3_s4nta_m4de_4_m1stak3_sorry}<br></pre>
<!-- /wp:preformatted -->

<!-- wp:separator -->
<hr class="wp-block-separator"/>
<!-- /wp:separator -->

<!-- wp:paragraph -->
<p>Đó là toàn bộ những bài mình giải ra trong giải CTF này. Cảm ơn các bạn đã đọc!<br></p>
<!-- /wp:paragraph -->
