---
title: 連結器工具錯誤 LNK1211 |Microsoft 文件
ms.date: 12/05/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1211
dev_langs:
- C++
helpviewer_keywords:
- LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57948556ae7b94b9a1788b7cb4453646b5b504f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1211"></a>連結器工具錯誤 LNK1211

> 找不到; 先行編譯的類型資訊'*filename*' 未連結或覆寫

*Filename*使用編譯的目的檔[/Yc](../../build/reference/yc-create-precompiled-header-file.md)、 LINK 命令中未指定，或已被覆寫。

如果您要建立偵錯程式庫使用先行編譯標頭，並指定 **/Yc**和[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)，Visual c + + 產生先行編譯的物件檔案包含偵錯資訊。 只有當您先行編譯的物件檔儲存在文件庫時，發生錯誤、 使用程式庫來建置可執行映像，和所參考的物件檔案具有不到任何函式的先行編譯的物件檔案會定義可轉移的參考。

有兩種方法可以解決此問題：

- 指定[/Yd](../../build/reference/yd-place-debug-information-in-object-file.md)編譯器選項，將先行編譯標頭中加入每個物件模組的偵錯資訊。 這個方法是較不理想，因為它通常會產生大型物件模組，增加連結應用程式所需的時間。

- 指定[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)和傳遞的任意字串，名稱，當您建立不包含任何函式定義的先行編譯標頭檔。 這會指示編譯器建立先行編譯的目的檔中的符號，並發出每個使用先行編譯標頭檔與先行編譯的物件檔案相關聯的物件檔案中該符號的參考。

當您編譯同名的模組 **/Yc**和 **/Yl**，類似的編譯器建立符號`__@@_PchSym_@00@...@symbol_name`，其中的省略符號 （...） 代表編譯器產生的字元字串，並將其儲存在物件的模組。 指定的符號，這會導致連結器包含此物件模組和程式庫的偵錯資訊是指您此先行編譯標頭使用編譯任何原始程式檔。
