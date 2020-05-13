---
title: 轉譯：診斷
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: a274b7c5f29b091b2bf29922abfa4d66d3447b47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344963"
---
# <a name="translation-diagnostics"></a>轉譯：診斷

**ANSI 2.1.1.3** 如何識別診斷

Microsoft C 會產生下列格式的錯誤訊息：

> *檔案名* **（** *行號* **）：** *診斷* **C**<em>數位</em>*訊息*

其中 *filename* 是發生錯誤所在的來源檔案名稱，*line-number* 是編譯器偵測到錯誤的行號，*diagnostic* 是「錯誤」或「警告」，*number* 是用於識別錯誤或警告的唯一四位數字 (前面加上 **C**，如語法中所註解)，而 *message* 是說明訊息。

## <a name="see-also"></a>請參閱

[實作定義的行為](../c-language/implementation-defined-behavior.md)
