---
title: 編譯器錯誤 C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 69f0544815804e9827631be81bf9735a95bd1a22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176698"
---
# <a name="compiler-error-c3012"></a>編譯器錯誤 C3012

> '*內建 '：* 內建函式不能直接在平列區域內使用

[編輯器內部](../../intrinsics/compiler-intrinsics.md) 區域中不允許 `omp parallel` 函式。 若要修正此問題，請將內建函式移出區域，或將其取代為非內建函式的對等專案。

## <a name="example"></a>範例

下列範例會產生 C3012，並顯示解決此問題的一種方法：

```cpp
// C3012.cpp
// compile with: /openmp
#ifdef __cplusplus
extern "C" {
#endif
void* _ReturnAddress();
#ifdef __cplusplus
}
#endif

int main()
{
   #pragma omp parallel
   {
      _ReturnAddress();   // C3012
   }
   _ReturnAddress();      // OK
}
```
