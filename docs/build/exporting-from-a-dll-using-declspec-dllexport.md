---
title: 使用 __declspec(dllexport) 從 DLL 匯出
ms.date: 05/06/2019
f1_keywords:
- dllexport
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 075962758773660085ae0b98b668c264524cc6aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328587"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>使用 __declspec(dllexport) 從 DLL 匯出

您可以使用 **__declspec （dllexport）** 關鍵字，從 DLL 匯出資料、函式、類別或類別成員函式。 **__declspec （dllexport）** 會將 export 指示詞加入至目的檔，因此您不需要使用 .def 檔案。

當您嘗試匯出裝飾的 c + + 函式名稱時，這是最明顯的便利性。 因為沒有名稱裝飾的標準規格，所以匯出函式的名稱可能會在編譯器版本之間變更。 如果您使用 **__declspec （dllexport）**，則只需要重新編譯 DLL 和相依的 .exe 檔案，以考慮任何命名慣例的變更。

許多匯出指示詞（例如序數、NONAME 和私用）只能在 .def 檔案中進行，而且沒有任何方法可以在不使用 .def 檔的情況下指定這些屬性。 不過，除了使用 .def 檔案之外，使用 **__declspec （dllexport）** 並不會造成組建錯誤。

若要匯出函式，如果已指定關鍵字，則 **__declspec （dllexport）** 關鍵字必須出現在呼叫慣例關鍵字的左邊。 例如：

```
__declspec(dllexport) void __cdecl Function1(void);
```

若要匯出類別中的所有公用資料成員和成員函式，關鍵字必須出現在類別名稱的左邊，如下所示：

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)`無法套用至具有`__clrcall`呼叫慣例的函式。

建立 DLL 時，您通常會建立標頭檔，其中包含您要匯出的函式原型和/或類別，並將 **__declspec （dllexport）** 新增至標頭檔中的宣告。 若要讓您的程式碼更容易閱讀，請為 **__declspec （dllexport）** 定義宏，並使用宏搭配您要匯出的每個符號：

```
#define DllExport   __declspec( dllexport )
```

**__declspec （dllexport）** 會在 DLL 的匯出資料表中儲存函數名稱。 如果您想要優化資料表的大小，請參閱[依序數而不是依名稱匯出 DLL 中的函數](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [使用 .def 檔從 DLL 匯出](exporting-from-a-dll-using-def-files.md)

- [使用 AFX_EXT_CLASS 匯出和匯入](exporting-and-importing-using-afx-ext-class.md)

- [匯出 c + + 函式以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [匯出 C 函式以用於 C 或 c + + 語言可執行檔](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [__Declspec 關鍵字](../cpp/declspec.md)

- [匯入和匯出內嵌函式](importing-and-exporting-inline-functions.md)

- [相互匯入](mutual-imports.md)

## <a name="see-also"></a>請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
