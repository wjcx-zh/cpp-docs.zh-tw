---
title: 連結器工具錯誤 LNK1211
ms.date: 12/05/2017
f1_keywords:
- LNK1211
helpviewer_keywords:
- LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
ms.openlocfilehash: 7c918cacb87460c2aad30285b750d9b170425534
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456143"
---
# <a name="linker-tools-error-lnk1211"></a>連結器工具錯誤 LNK1211

> 找不到; 的先行編譯的類型資訊'*filename*' 未連結或覆寫

*檔名*使用編譯的目的檔[/Yc](../../build/reference/yc-create-precompiled-header-file.md)、 連結 命令中未指定，或已被覆寫。

如果您要建立偵錯程式庫使用先行編譯標頭，並指定 **/Yc**並[/z7](../../build/reference/z7-zi-zi-debug-information-format.md)，Visual c + + 產生的先行編譯的物件檔案包含偵錯資訊。 只有當您先行編譯的物件檔案存放在程式庫時，發生錯誤、 使用程式庫來建置可執行檔映像，和所參考的物件檔案具有不到任何函式的先行編譯的物件檔案會定義可轉移的參考。

有兩種方法可以解決此問題：

- 指定[/Yd](../../build/reference/yd-place-debug-information-in-object-file.md)編譯器選項，從 先行編譯標頭中將每個物件模組的偵錯資訊。 這個方法是相較，因為它通常會產生大型物件模組，可增加連結應用程式所需的時間。

- 指定[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)並傳遞任何任意的字串名稱，當您建立不包含任何函式定義的先行編譯標頭檔。 這會指示編譯器建立先行編譯的目的檔中的符號，並發出每個使用先行編譯的物件檔案與相關聯的先行編譯標頭檔的目的檔中該符號的參考。

當您編譯模組 **/Yc**並 **/Yl**，類似的編譯器建立符號`__@@_PchSym_@00@...@symbol_name`，其中的省略符號 （...） 代表編譯器所產生的字元字串，並將其儲存在物件模組。 指定的符號，這會導致連結器包含此物件模組和程式庫的偵錯資訊是指您使用此先行編譯標頭檔編譯任何原始程式檔。
