---
title: 嚴重錯誤 C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: bb1d9af10084d6b3e75325450c7f13ea1683ee2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229042"
---
# <a name="fatal-error-c1128"></a>嚴重錯誤 C1128

區段數目超過目的檔格式的限制： 請以 /bigobj 編譯

.Obj 檔超過允許的區段，COFF 物件檔案格式限制的數目。

此區段限制可使用的結果[/Gy](../../build/reference/gy-enable-function-level-linking.md)和偵錯組建中;**/Gy**會導致函式進入自己的 COMDAT 區段。 在偵錯組建中，沒有針對每個 COMDAT 函式的偵錯資訊 區段。

有太多的內嵌函式時，也可能造成 C1128。

若要更正這個錯誤，分成多個原始程式碼檔中的原始程式檔、 編譯而不需 **/Gy**，或使用編譯[/bigobj （增加中的區段數目。Obj 檔）](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)。  如果您使用未編譯 **/Gy**，您必須指定個別的最佳化由於 **/o2**並 **/o1**都隱含 **/Gy**。

可能的話，請編譯但不偵錯資訊。

您可能也需要在個別的原始程式碼檔案中，有特定的具現化的範本，而不是由編譯器發出這些。

當移植程式碼，C1128 可能最先出現時使用 x64 編譯器，而使用 x86 編譯器。 x64 會有 4 個以上的區段與編譯每個函式相關聯 **/Gy**或從樣板內嵌或類別內嵌： 程式碼、 pdata 和偵錯資訊，可能還有 xdata。  X86 不用 pdata。