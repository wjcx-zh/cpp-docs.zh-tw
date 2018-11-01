---
title: PROTO
ms.date: 10/22/2018
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 616b6be2a5c191ebc67d61288cb5fa6c183091fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536704"
---
# <a name="proto"></a>PROTO

原型的函式或程序。 您可以呼叫此函式原型 PROTO 指示詞所使用[INVOKE](invoke.md)指示詞。

## <a name="syntax"></a>語法

> *標籤* **PROTO** \[*距離*] \[ *langtype*] \[ __，__ \[*參數*]__:__*標記*]...

### <a name="parameters"></a>參數

*標籤*<br/>
原型的函式的名稱。

*distance*<br/>
（選擇性）16 位元記憶體中模型中使用覆寫預設值，並指出**NEAR**或是**FAR**呼叫。

*langtype*<br/>
（選擇性）設定程序和公用符號的呼叫和命名慣例。 支援的慣例如下：

- 32 位元**平面**模型： **C**， **STDCALL**

- 16 位元模型： **C**， **BASIC**， **FORTRAN**， **pascal 命名法**， **SYSCALL**， **STDCALL**

*parameter*<br/>
函式參數的選擇性名稱。

*標記*<br/>
函式參數的型別。

*參數*並*標記*參數可能會出現許多次，一次的每個傳遞的引數。

## <a name="example"></a>範例

這個範例會示範**PROTO**名為函式宣告`addup3`使用**NEAR**呼叫程序呼叫，並使用的 16 位元模型預設值會覆寫**C**呼叫慣例的 stack 參數和傳回值。 它會採用兩個引數， **WORD**並**VARARG**。

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>另請參閱

[指示詞參考](directives-reference.md)<br/>
[.模型參考](dot-model.md)<br/>
