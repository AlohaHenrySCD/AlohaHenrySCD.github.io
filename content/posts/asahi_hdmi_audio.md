+++
date = '2026-10-25T22:26:09+08:00'
draft = true
title = 'Asahi HDMI Audio'
+++
drivers/dma/apple-sio.c中
由于SIO_NO_DESC_SLOTS被定义为64（我不知道是不是由apple决定的）
因此nperiods至多为64个（应该说所有传输共享64个描述符槽位）

他由buf_len/period_len得来

后来发现nperiods其实是有限制的，但是写的是uint max，相当于没有，修改后测试，果然解决了问题，试着提交pr去了
