---
title: 連結器工具錯誤 LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: a267019f1be08cc8dcffdff3b4ba0b73357cccd4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183953"
---
# <a name="linker-tools-error-lnk1179"></a>連結器工具錯誤 LNK1179

檔案無效或損毀：重複的 COMDAT ' filename '

物件模組包含兩個或多個具有相同名稱的 Comdat。

這個錯誤可能是因為使用[/h](../../build/reference/h-restrict-length-of-external-names.md)（限制外部名稱的長度）和[/Gy](../../build/reference/gy-enable-function-level-linking.md)（封裝 comdat 中的函數）所造成。

## <a name="example"></a>範例

在下列程式碼中，前八個字元的 `function1` 和 `function2` 都相同。 以 **/gy**和 **/H8**編譯會產生連結錯誤。

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
