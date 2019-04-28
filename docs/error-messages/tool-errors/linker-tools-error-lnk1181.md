---
title: 連結器工具錯誤 LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: 657e78ece2ce4039eb8dc8561abd455c60aaff75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62254909"
---
# <a name="linker-tools-error-lnk1181"></a>連結器工具錯誤 LNK1181

無法開啟輸入的檔 'filename'

連結器找不到`filename`因為它不存在或找不到路徑。

錯誤 LNK1181 包含一些常見原因：

- `filename` 被參考，因為其他的相依性連結器列，但該檔案不存在。

- A **/LIBPATH**陳述式，指定目錄包含`filename`遺失。

若要解決上述問題，請確定任何參考連結器列上的檔案是存在於系統上。  也請確定沒有 **/LIBPATH**陳述式，針對每個包含連結器相依檔案的目錄。

如需詳細資訊，請參閱 < [.lib 檔作為連結器輸入](../../build/reference/dot-lib-files-as-linker-input.md)。

Lnk1181 另一個可能的原因是不允許有空白字元的長檔名不以引號括住。  在此情況下，連結器會只辨識檔案名稱最多的第一個空間，並採用檔案的副檔名。 obj這種情況的解決方案是來括住的長檔名 （路徑加上檔案名稱） 以引號。

在以編譯[/P （前置處理至檔案）](../../build/reference/p-preprocess-to-a-file.md)選項可能會導致 LNK1181 因為該選項會抑制.obj 檔案的建立。

## <a name="see-also"></a>另請參閱

[/LIBPATH (其他 Libpath)](../../build/reference/libpath-additional-libpath.md)