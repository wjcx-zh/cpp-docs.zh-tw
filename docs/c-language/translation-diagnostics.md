---
title: 轉譯：診斷
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: 4863b97dc1db7ff295b5f786ca97da2551d0fa62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664993"
---
# <a name="translation-diagnostics"></a>轉譯：診斷

**ANSI 2.1.1.3** 如何識別診斷

Microsoft C 會產生下列格式的錯誤訊息：

> *filename* **(** *line-number* **) :** *diagnostic* **C**<em>number</em> *message*

其中 *filename* 是發生錯誤所在的來源檔案名稱，*line-number* 是編譯器偵測到錯誤的行號，*diagnostic* 是「錯誤」或「警告」，*number* 是用於識別錯誤或警告的唯一四位數字 (前面加上 **C**，如語法中所註解)，而 *message* 是說明訊息。

## <a name="see-also"></a>請參閱

[實作定義的行為](../c-language/implementation-defined-behavior.md)