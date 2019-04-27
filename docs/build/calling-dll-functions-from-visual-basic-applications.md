---
title: 從 Visual Basic 應用程式中呼叫 DLL 函式
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
ms.openlocfilehash: 1e4f1a538da2394c6cead6ea011faf126b022a3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195338"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>從 Visual Basic 應用程式中呼叫 DLL 函式

Visual Basic 應用程式 （或應用程式，以其他語言，例如 Pascal 或 Fortran） 呼叫中的 C 函式 /C++ DLL，必須使用正確的呼叫慣例，而不需要任何名稱裝飾，由編譯器匯出的函式

`__stdcall` 建立函式的正確呼叫慣例 （呼叫的函式會清除堆疊和由右至左傳遞參數），但以不同的方式來修飾函式名稱。 因此，當 **__declspec （dllexport)** 用在 DLL 中的匯出函式，會匯出裝飾的名稱。

`__stdcall`名稱裝飾前置詞符號名稱以底線 ( **\_** )，並將附加的符號寬度 at 符號 (**\@**) 字元後面的數目引數清單 （所需的堆疊空間） 中的位元組。 如此一來，當宣告為函式：

```C
int __stdcall func (int a, double b)
```

就會裝飾成`_func@12`在輸出中。

C 呼叫慣例 (`__cdecl`) 將做為名稱裝飾`_func`。

若要取得裝飾的名稱，請使用[/typedefs/ 對應](reference/map-generate-mapfile.md)。 利用 **__declspec （dllexport)** 會進行下列作業：

- 如果以 C 呼叫慣例匯出函式 (`__cdecl`)，它會移除前置底線 ( **\_** ) 會匯出名稱。

- 如果要匯出的函式不使用 C 呼叫慣例 (例如`__stdcall`)，它會匯出裝飾的名稱。

因為沒有任何方法來覆寫堆疊清除發生的位置，您必須使用`__stdcall`。 若要有名稱`__stdcall`，您必須在.def 檔的 EXPORTS 區段裡使用別名來指定它們。 這會為下列函式宣告，如下所示顯示：

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

在中。DEF 檔案：

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

本主題所示的別名技術在 Visual Basic 中撰寫的程式所呼叫的 Dll，需要.def 檔案中。 如果別名是在 Visual Basic 程式中，就不需要使用.def 檔案中的別名。 也可以在 Visual Basic 程式中加入別名子句[Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)陳述式。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [從 DLL 匯出](exporting-from-a-dll.md)

- [匯出從 DLL 使用。DEF 檔](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [匯出C++函式以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [裝飾的名稱](reference/decorated-names.md)

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](dlls-in-visual-cpp.md)
