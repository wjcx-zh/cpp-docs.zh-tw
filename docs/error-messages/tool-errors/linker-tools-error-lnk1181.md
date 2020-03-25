---
title: 連結器工具錯誤 LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: d2b28af52a2ca2263a7bad77c8c69242396ff2b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195249"
---
# <a name="linker-tools-error-lnk1181"></a>連結器工具錯誤 LNK1181

無法開啟輸入檔 ' filename '

連結器找不到 `filename`，因為它不存在，或找不到路徑。

錯誤 LNK1181 的一些常見原因包括：

- `filename` 參考為連結器行上的其他相依性，但檔案不存在。

- **/LIBPATH**語句，指定遺失包含 `filename` 的目錄。

若要解決上述問題，請確定連結器行上所參考的任何檔案都存在於系統上。  此外，也請確定每個包含連結器相依檔案的目錄都有一個 **/LIBPATH**語句。

如需詳細資訊，請參閱[.lib 檔案做為連結器輸入](../../build/reference/dot-lib-files-as-linker-input.md)。

LNK1181 的另一個可能原因是，具有內嵌空格的長檔名不會括在引號中。  在此情況下，連結器只會辨識最多到第一個空格的檔案名，然後假設副檔名為 .obj。 這種情況的解決方法是以引號括住長的檔案名（路徑加上檔案名）。

使用[/p （](../../build/reference/p-preprocess-to-a-file.md)前置處理至檔案）選項進行編譯，可能會導致 LNK1181，因為該選項會隱藏 .obj 檔案的建立。

## <a name="see-also"></a>另請參閱

[/LIBPATH (其他 Libpath)](../../build/reference/libpath-additional-libpath.md)
