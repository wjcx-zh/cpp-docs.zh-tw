---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: a30840aa0556a7324ba24c0f2aaec57dea88d082
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367860"
---
# <a name="noreturn"></a>noreturn

**Microsoft 特定的**

此 **__declspec**屬性告訴編譯器函數不返回。 因此,編譯器知道調用 **__declspec(返回)** 函數後的代碼是無法訪問的。

如果編譯器發現某個函式包含的控制路徑不會傳回值，則會產生警告 (C4715) 或錯誤訊息 (C2202)。 如果由於函數永遠不會返回而無法訪問控制路徑,則可以使用 **__declspec(不返回)** 來防止此警告或錯誤。

> [!NOTE]
> 向預期返回的函數添加 **__declspec(不返回)** 可能會導致未定義的行為。

## <a name="example"></a>範例

在下面的範例中,**其他**子句不包含返回語句。  聲明`fatal`為 **__declspec(不返回)** 可避免錯誤或警告消息。

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

**結束微軟的**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
