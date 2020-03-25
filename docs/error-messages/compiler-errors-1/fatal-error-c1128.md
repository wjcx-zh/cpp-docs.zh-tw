---
title: 嚴重錯誤 C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: 64671c9abe8ed1375df1e91ca7509e6a597366ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203622"
---
# <a name="fatal-error-c1128"></a>嚴重錯誤 C1128

區段數超過物件檔案格式限制：使用/bigobj 進行編譯

.Obj 檔案超過允許的區段數，也就是 COFF 物件檔案格式的限制。

達到這個區段的限制可能是使用[/gy](../../build/reference/gy-enable-function-level-linking.md)和 debug 組建的結果; **/Gy**會使函數進入自己的 COMDAT 區段。 在 debug 組建中，每個 COMDAT 函式都有一個 debug info 區段。

當內嵌函數太多時，也可能會造成 C1128。

若要更正這個錯誤，請將您的原始程式檔分成多個原始程式碼檔、編譯不加 **/gy**，或使用/bigobj 進行編譯[（增加中的區段數）。Obj 檔案）](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)。  如果您不使用 **/gy**進行編譯，就必須個別指定優化，因為 **/O2**和 **/O1**兩者都是 **/gy**。

可能的話，請編譯而不進行任何調試資訊。

您可能也需要在不同的原始程式碼檔案中有範本的特定具現化，而不是讓編譯器發出它們。

移植程式碼時，C1128 可能會在使用 x64 編譯器時先出現，並在稍後使用 x86 編譯器時顯示。 x64 至少會有4個區段與每個編譯的 **/gy**或從範本或類別內嵌的函式建立關聯： code、pdata 和 debug info，而且可能 .xdata。  X86 不會有 pdata。
