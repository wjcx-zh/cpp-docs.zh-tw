---
title: 編譯器錯誤 C2555
description: 視覺工作室C++編譯器錯誤 C2555 的參考。
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: fe0e6379e783387506e6098c9b14a047baa8e6c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374179"
---
# <a name="compiler-error-c2555"></a>編譯器錯誤 C2555

> '*類別 1*::*函數 1':* 重寫虛擬函數傳回類型不同,並且不是從 '*類別2*::*函數2*'

虛擬函數和派生重寫函數具有相同的參數清單,但返回類型不同。

## <a name="remarks"></a>備註

在C++中,派生類中重寫函數不能僅因返回類型與基類中的虛擬函數不同而不同。

對於某些返回類型,此規則有一個例外。 當派生類重寫公共基類時,它可以返回指向派生類的指標或引用,而不是基類指標或引用。 這些返回類型稱為*協變數*,因為它們隨類型而變化。 此規則異常不允許對指標或指標類型的協變數引用。

解決錯誤的一種方法是返回與基類相同的類型。 然後,在調用虛擬函數后強制轉換返回值。 另一種是更改參數清單,使派生類成員函數成為重載函數,而不是重寫。

## <a name="examples"></a>範例

如果使用 編譯,則可能會看到此**`/clr`** 錯誤 。 例如,等效於以下 C# 聲明C++:

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

以下範例產生 C2555:

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```

要修復它,將傳`Y::func`回型態`void`變更為 。
