---
title: 裝飾名稱
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: c7821fc9fca1c9a965ea83584415b9baf17ec683
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579100"
---
# <a name="decorated-names"></a>裝飾名稱

C 和 C++ 程式中的函式、資料和物件在內部以其裝飾名稱表示。 A*裝飾名稱*是編譯器所編譯的物件、 資料或函式定義期間建立為編碼的字串。 它會記錄呼叫慣例、類型、函式參數和其他資訊，並連同名稱一起記錄。 此名稱裝飾，也稱為*名稱改編*、 協助連結器尋找正確的函式和物件連結可執行檔時。

裝飾命名慣例在各種版本的 Visual C++ 中已變更，而且在不同的目標架構上也可能不同。 若要正確連結使用 Visual C++ 所建立的原始程式檔，應該使用相同的編譯器工具組、旗標和目標架構來編譯 C 和 C++ Dll 和程式庫。

##  <a name="Using"></a> 使用裝飾名稱

通常，您在撰寫程式碼時不必知道裝飾名稱，也能成功編譯和連結。 裝飾名稱是編譯器和連結器內部的實作詳細資料。 這些工具通常能夠處理未裝飾的名稱。 不過，當您指定函式名稱給連結器和其他工具時，有時需要裝飾名稱。 比方說，若要符合多載 C++ 函式、命名空間的成員、類別建構函式、解構函式和特殊成員函式，您必須指定裝飾名稱。 如需選項旗標和其他需要裝飾名稱的情況的詳細資訊，請參閱您要使用的工具和選項的文件。

如果您變更函式名稱、類別、呼叫慣例、傳回類型或任何參數，裝飾名稱也會變更。 在此情況下，您必須取得新的裝飾名稱，並在指定裝飾名稱的每個地方使用。

在連結至以其他程式設計語言撰寫的程式碼或使用其他編譯器時，名稱裝飾也很重要。 不同編譯器會使用不同的名稱裝飾慣例。 當您的執行檔連結至以另一種語言撰寫的程式碼時，必須特別注意符合匯出和匯入的名稱和呼叫慣例。 組件語言程式碼必須使用 Visual C++ 裝飾名稱和呼叫慣例，才能連結至使用 Visual C++ 撰寫的原始程式碼。

##  <a name="Format"></a> 裝飾名稱的 c + + 格式。

C++ 函式的裝飾名稱包含下列資訊：

- 函式名稱。

- 函式所屬的類別 (如果是成員函式)。 其中類別可能還包含另一個類別，而該類別包含函式等。

- 函式所屬的命名空間 (如果是命名空間的一部分)。

- 函式參數的類型。

- 呼叫慣例。

- 函式的傳回型別。

函式和類別名稱是以裝飾名稱編碼。 裝飾名稱的其餘部分是只在編譯器和連結器內部才有意的代碼。 以下是 C++ 未裝飾和裝飾名稱的範例。

|未裝飾名稱|裝飾名稱|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

##  <a name="FormatC"></a> 裝飾名稱的 C 格式。

C 函式的裝飾形式取決於它的宣告中所使用的呼叫慣例，如下表所示。 這也是 C++ 程式碼宣告為有 `extern "C"` 連結時所使用的裝飾格式。 預設呼叫慣例是 `__cdecl`。 請注意，在 64 位元環境中，函式未裝飾。

|呼叫慣例|裝飾|
|------------------------|----------------|
|`__cdecl`|前置底線 (**_**)|
|`__stdcall`|前置底線 (**_**) 和尾端正負號 (**\@**) 後面接著十進位格式的參數清單中的位元組數目|
|`__fastcall`|開頭和尾端 @ 符號 (**\@**) 後面接著十進位數字表示的參數清單中的位元組數目|
|`__vectorcall`|兩個尾端 @ 符號 (**\@\@**) 後面接著十進位數字的參數清單中的位元組|

##  <a name="Viewing"></a> 檢視裝飾名稱

在編譯包含資料、物件或函式定義或原型的原始程式檔之後，您可以取得裝飾形式的符號名稱。 若要檢查您程式中的裝飾名稱，您可以使用下列任何一個方法：

#### <a name="to-use-a-listing-to-view-decorated-names"></a>使用清單檢視裝飾名稱

1. 編譯包含資料、 物件或函式定義或原型的原始程式檔，以產生清單[列出檔案類型](../../build/reference/fa-fa-listing-file.md)編譯器選項設定為含有原始程式碼的組件 (**/FAs**)。

   例如，輸入`cl /c /FAs example.cpp`開發人員命令提示字元來產生清單檔 example.asm。

2. 在結果清單檔案中，尋找開頭是 PUBLIC 和結尾是分號且後面是未裝飾資料或函式名稱的那一行。 PUBLIC 和分號之間的符號就是裝飾名稱。

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>使用 DUMPBIN 檢視裝飾名稱

1. 若要查看.obj 或.lib 檔案中匯出的符號，請輸入`dumpbin /symbols``objfile`的開發人員命令提示字元。

2. 若要尋找裝飾形式的符號，請尋找括號中的未裝飾名稱。 裝飾的名稱是在同一行之後管道, (&#124;) 字元和未裝飾名稱之前。

##  <a name="Undecorated"></a> 檢視未裝飾名稱

您可以使用 undname.exe 將裝飾名稱轉換成未裝飾形式。 此範例示範它的運作方式：

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>另請參閱

[C/C++ 建置工具](../../build/reference/c-cpp-build-tools.md)<br/>
[使用 extern 指定連結](../../cpp/using-extern-to-specify-linkage.md)