---
title: ML 錯誤訊息
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: aa0440afae980e218c32ab3296bd7c6fb2b444d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62202207"
---
# <a name="ml-error-messages"></a>ML 錯誤訊息

MASM 元件所產生的錯誤訊息會分成三個類別：

- **嚴重錯誤。** 這些資訊表示嚴重的問題，導致無法完成其正常的處理序的公用程式。

- **非嚴重錯誤。** 此公用程式可能會完成其處理程序。 若是如此，不可能是您想的要其結果。

- **此警告。** 這些訊息表示條件，可能會導致無法取得您想要的結果。

所有的錯誤訊息的形式如下：

> *公用程式*:*檔名*(*線條*): {*Error_type*} (*程式碼*):*Message_text*

其中：

*公用程式*<br/>
傳送錯誤訊息的程式。

*檔案名稱*<br/>
包含產生錯誤條件的檔案。

*程式碼*<br/>
在錯誤狀況存在大約行。

*Error_type*<br/>
嚴重錯誤、 錯誤或警告。

*程式碼*<br/>
唯一 5 或 6 位元錯誤的程式碼。

*Message_text*<br/>
簡短和一般錯誤條件的描述。

## <a name="see-also"></a>另請參閱

[Microsoft 巨集組譯工具參考](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>