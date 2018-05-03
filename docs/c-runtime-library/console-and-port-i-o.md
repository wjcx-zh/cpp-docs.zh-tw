---
title: 主控台和連接埠 I/O | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- routines, console and port I/O
- routines
- ports, I/O routines
- I/O [CRT], console
- I/O [CRT], port
- I/O routines, console and port I/O
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db5532b35e915f69927699ce9678d5bd5ffb5579
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="console-and-port-io"></a>主控台和連接埠 I/O

這些常式會在您的主控台或指定的連接埠上進行讀取和寫入。 主控台 I/O 常式與資料流 I/O 或低層級 I/O 程式庫常式並不相容。 主控台或連接埠在執行 I/O 之前並不需要開啟或關閉，因此本類別中不會有 Open 或 Close 常式。 在 Windows 作業系統中，來自這些函式的輸出將會一律導向主控台，而無法重新導向。

## <a name="console-and-port-io-routines"></a>主控台和連接埠 I/O 常式

|常式傳回的值|使用|
|-------------|---------|
|[_cgets、_cgetws](../c-runtime-library/cgets-cgetws.md)、[_cgets_s、_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|從主控台讀取字串|
|[_cprintf、_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)、[_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|將格式化資料寫入主控台|
|[_cputs](../c-runtime-library/reference/cputs-cputws.md)|將字串寫入主控台|
|[_cscanf、_cwscanf](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)、[_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|從主控台讀取格式化資料|
|[_getch、_getwch](../c-runtime-library/reference/getch-getwch.md)|從主控台讀取字元|
|[_getche、_getwche](../c-runtime-library/reference/getch-getwch.md)|從主控台讀取字元並回應它|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|從指定的 I/O 連接埠讀取一個位元組|
|[_inpd](../c-runtime-library/inp-inpw-inpd.md)|從指定的 I/O 連接埠讀取雙字組|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|從指定的 I/O 連接埠讀 2 個位元組文字|
|[_kbhit](../c-runtime-library/reference/kbhit.md)|在主控台檢查按鍵輸入，於嘗試從主控台讀取前使用|
|[_outp](../c-runtime-library/outp-outpw-outpd.md)|將一個位元組寫入指定的 I/O 連接埠|
|[_outpd](../c-runtime-library/outp-outpw-outpd.md)|將雙字組寫入指定的 I/O 連接埠|
|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|將文字寫入指定的 I/O 連接埠|
|[_putch、_putwch](../c-runtime-library/reference/putch-putwch.md)|將字元寫入主控台|
|[_ungetch、_ungetwch](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|「取消取得」從主控台讀取的最後一個字元，使它成為要讀取的下一個字元|

## <a name="see-also"></a>請參閱

[輸入和輸出](../c-runtime-library/input-and-output.md)<br/>
 [依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>