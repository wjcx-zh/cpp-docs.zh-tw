---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: 38346e41c1e943e9bfda70668a163c630a0b9599
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178869"
---
# <a name="selectany"></a>selectany

**Microsoft 專屬**

告訴編譯器宣告的全域資料項目 (變數或物件) 是挑選任一個 (Pick-any) COMDAT (封裝函式)。

## <a name="syntax"></a>語法

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>備註

在連結時，如果看見多個定義的 COMDAT，則連結器會挑選一個定義並捨棄其餘定義。 如果選取了連結器選項[/opt： REF](../build/reference/opt-optimizations.md) （優化），則會發生 COMDAT 刪除，以移除連結器輸出中所有未參考的資料項目。

宣告中的建構函式以及由全域函式或靜態方法進行的指派不會建立參考，也不會阻止 /OPT:REF 刪除作業。 來自這類程式碼的副作用不應取決於不存在其他資料參考時。

對於動態初始化的全域物件， **selectany**也會捨棄未參考物件的初始化程式碼。

全域資料項目通常只能在 EXE 或 DLL 專案中初始化一次。 當同一個標頭出現在多個原始程式檔時，可以使用**selectany**來初始化標頭所定義的全域資料。 **selectany**同時適用于 C 和C++編譯器。

> [!NOTE]
>  **selectany**只能套用至外部可見的全域資料項目實際初始化。

## <a name="example"></a>範例

此程式碼說明如何使用**selectany**屬性：

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

這段程式碼示範如何使用**selectany**屬性，在您同時使用[/opt： ICF](../build/reference/opt-optimizations.md)連結器選項時，確保資料 COMDAT 折迭。 請注意，資料必須以**selectany**標記，並放在**const** （readonly）區段中。 您必須明確指定唯讀區段。

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

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
