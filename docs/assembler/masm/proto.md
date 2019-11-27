---
title: PROTO
ms.date: 10/22/2018
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 24ec2a9abc6c8b76fc81f6d412019296c53160f4
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74394761"
---
# <a name="proto"></a>PROTO

原型函數或程式。 您可以使用[INVOKE](invoke.md)指示詞，透過 PROTO 指示詞呼叫函數原型。

## <a name="syntax"></a>語法

> *標籤* **PROTO** ⟦*距離*⟧ *⟦ language-類型*⟧⟦ __，__ ⟦*參數*⟧ __：__ *標記*.。。⟧

### <a name="parameters"></a>參數

*標籤*\
原型函式的名稱。

*距離*\
選擇性在16位記憶體模型中用來覆寫預設值，並指出**接近**或**遠**的呼叫。

*語言類型*\
選擇性設定程式和公用符號的呼叫和命名慣例。 支援的慣例如下：

- 32位**平面**模型： **C**、 **STDCALL**

- 16位模型： **C**、**基本**、 **FORTRAN**、 **PASCAL**、 **SYSCALL**、 **STDCALL**

*參數*\
函數參數的選擇性名稱。

*標記*\
函數參數的類型。

*參數*和*標記*參數可能會多次出現，每個傳遞的引數一次。

## <a name="example"></a>範例

這個範例會顯示名為 `addup3` 之函式的**PROTO**宣告，此函式會使用**接近**呼叫來覆寫程序呼叫的16位模型預設值，並使用堆疊參數和傳回值的**C**呼叫慣例。 它接受兩個引數：一個**單字**和一個**VARARG**。

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>另請參閱

指示詞[參考](directives-reference.md)\
[.模型參考](dot-model.md)
