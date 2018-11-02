---
title: 連結器工具錯誤 LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: 71aba1f20cfaf5b6b9ec33d43ebde594e381921f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594086"
---
# <a name="linker-tools-error-lnk1179"></a>連結器工具錯誤 LNK1179

檔案無效或損毀： 重複的 COMDAT 'filename'

物件模組包含兩個或多個具有相同名稱的 Comdat。

此錯誤可能因使用[/H](../../build/reference/h-restrict-length-of-external-names.md)，這會限制外部名稱的長度並[/Gy](../../build/reference/gy-enable-function-level-linking.md)，哪些套件中的 Comdat 函式。

## <a name="example"></a>範例

下列程式碼中，`function1`和`function2`是相同的前八個字元。 在以編譯 **/Gy**並 **/h8 編譯**會產生連結錯誤。

```
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```