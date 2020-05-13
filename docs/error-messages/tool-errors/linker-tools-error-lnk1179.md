---
title: 連結器工具錯誤 LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: d85693cec11ef53a6bbbb60d8ced716d2a0bb131
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754342"
---
# <a name="linker-tools-error-lnk1179"></a>連結器工具錯誤 LNK1179

無效或損壞的檔:重複COMDAT"檔名"

物件模組包含兩個或多個具有相同名稱的 COMDAT。

此錯誤可能由使用[/H(](../../build/reference/h-restrict-length-of-external-names.md)限制外部名稱的長度)和[/Gy](../../build/reference/gy-enable-function-level-linking.md)(在 COMDATs 中)進行打包函數引起。

## <a name="example"></a>範例

在以下代碼中,`function1``function2`在前八個字元中相同。 使用 **/Gy**和 **/H8**編譯會產生連結錯誤。

```cpp
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```
