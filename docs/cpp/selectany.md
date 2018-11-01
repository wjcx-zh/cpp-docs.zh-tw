---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: a6bf4076dfecbd29035716285f52c0a9faf81067
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623752"
---
# <a name="selectany"></a>selectany

**Microsoft 專屬**

告訴編譯器宣告的全域資料項目 (變數或物件) 是挑選任一個 (Pick-any) COMDAT (封裝函式)。

## <a name="syntax"></a>語法

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>備註

在連結時，如果看見多個定義的 COMDAT，則連結器會挑選一個定義並捨棄其餘定義。 如果連結器選項[/opt: ref](../build/reference/opt-optimizations.md) （最佳化） 已選取，則 COMDAT 刪除作業會移除所有未參考的資料的項目連結器輸出中。

宣告中的建構函式以及由全域函式或靜態方法進行的指派不會建立參考，也不會阻止 /OPT:REF 刪除作業。 來自這類程式碼的副作用不應取決於不存在其他資料參考時。

對於動態初始化的全域物件， **selectany**將會捨棄未參考的物件的初始化程式碼，以及。

全域資料項目通常只能在 EXE 或 DLL 專案中初始化一次。 **selectany**可用在初始化時相同的標頭會顯示一個以上的原始程式檔中，標頭所定義的全域資料。 **selectany**是在 C 和 c + + 編譯器中使用。

> [!NOTE]
>  **selectany**只能套用至外部可見的全域資料項目的實際初始化。

## <a name="example"></a>範例

此程式碼示範如何使用**selectany**屬性：

```cpp
//Correct - x1 is initialized and externally visible
__declspec(selectany) int x1=1;

//Incorrect - const is by default static in C++, so
//x2 is not visible externally (This is OK in C, since
//const is not by default static in C)
const __declspec(selectany) int x2 =2;

//Correct - x3 is extern const, so externally visible
extern const __declspec(selectany) int x3=3;

//Correct - x4 is extern const, so it is externally visible
extern const int x4;
const __declspec(selectany) int x4=4;

//Incorrect - __declspec(selectany) is applied to the uninitialized
//declaration of x5
extern __declspec(selectany) int x5;

// OK: dynamic initialization of global object
class X {
public:
X(int i){i++;};
int i;
};

__declspec(selectany) X x(1);
```

## <a name="example"></a>範例

此程式碼示範如何使用**selectany**屬性來確保資料的 COMDAT 摺疊時也使用[/opt: icf](../build/reference/opt-optimizations.md)連結器選項。 請注意，資料必須標示**selectany**並放置在**const** （唯讀） 區段。 您必須明確指定唯讀區段。

```cpp
// selectany2.cpp
// in the following lines, const marks the variables as read only
__declspec(selectany) extern const int ix = 5;
__declspec(selectany) extern const int jx = 5;
int main() {
   int ij;
   ij = ix + jx;
}
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)