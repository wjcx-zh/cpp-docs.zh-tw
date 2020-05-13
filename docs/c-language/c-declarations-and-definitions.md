---
title: C 宣告和定義
ms.date: 11/04/2016
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
ms.openlocfilehash: 3be9cd72e9f4dbad4d279cc1bb65dfb92a61cd42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326049"
---
# <a name="c-declarations-and-definitions"></a>C 宣告和定義

「宣告」會在特定變數、函式或類型及其屬性之間建立關聯。 [宣告概觀](../c-language/overview-of-declarations.md)中提供了 `declaration` 非終端項的 ANSI 語法。 宣告也會指定識別項可以存取的位置和時間 (識別項的「連結」)。 如需連結的詳細資訊，請參閱[存留期、範圍、可見度和連結](../c-language/lifetime-scope-visibility-and-linkage.md)。

變數的「定義」會建立與宣告相同的關聯，但也會為變數配置儲存區。

例如，`main`、`find` 和 `count` 函式，以及 `var` 和 `val` 變數是在某個原始程式檔中定義，順序如下：

```
int main() {}

int var = 0;
double val[MAXVAL];
char find( fileptr ) {}
int count( double f ) {}
```

變數 `var` 和 `val` 可用於 `find` 和 `count` 函式，不需要進一步宣告。 但是，這些名稱在 `main` 中是不可見的 (無法存取)。

## <a name="see-also"></a>請參閱

[原始程式檔和來源程式](../c-language/source-files-and-source-programs.md)
