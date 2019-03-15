---
title: 使用 __declspec(dllexport) 從 DLL 匯出
ms.date: 11/04/2016
f1_keywords:
- dllexport
- __declspec
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 3b6b9733776f30fc8dcbfeee709b7d24e0f0187b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810233"
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>使用 __declspec(dllexport) 從 DLL 匯出

Microsoft 推出 **__export** 16 位元編譯器版本的 Visual c + + 允許編譯器自動產生匯出名稱並將他們置於.lib 檔。 然後就像靜態.lib 來連結至 DLL 使用這個.lib 檔。

在新版本的編譯器，您可以匯出資料、 函數、 類別或類別成員函式從 DLL，使用 **__declspec （dllexport)** 關鍵字。 **__declspec （dllexport)** 將匯出指示詞加入至物件檔案，因此您不需要用到.def 檔。

嘗試匯出修飾 c + + 函式名稱時，這種便利性是最為明顯。 因為名稱裝飾無標準規格，匯出的函式的名稱可能會變更編譯器版本之間。 如果您使用 **__declspec （dllexport)**，重新編譯的 DLL 和相依的.exe 檔案是只需要在任何命名慣例的變更。

許多匯出指示詞，例如可只在.def 檔案中，序數、 NONAME 和 PRIVATE，且沒有辦法指定不使用.def 檔案而這些屬性。 不過，使用 **__declspec （dllexport)** 除了使用.def 檔不會造成建置錯誤。

若要匯出函式 **__declspec （dllexport)** 關鍵字必須呼叫慣例關鍵字左邊出現，如果指定的關鍵字。 例如: 

```
__declspec(dllexport) void __cdecl Function1(void);
```

若要匯出的所有公用資料成員和類別中的成員函式，關鍵字必須出現在類別名稱的左邊，如下所示：

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
>  `__declspec(dllexport)` 無法套用至的函式`__clrcall`呼叫慣例。

當建置您的 DLL，您通常可以建立包含函式原型和/或您要匯出，並加入的類別的標頭檔 **__declspec （dllexport)** 標頭檔中宣告。 若要讓您的程式碼更容易閱讀，定義為巨集 **__declspec （dllexport)** 和與每個您要匯出的符號使用巨集：

```
#define DllExport   __declspec( dllexport )
```

**__declspec （dllexport)** 存放區函式的 DLL 匯出表中的名稱。 如果您想要最佳化的資料表大小，請參閱[從根據序數而非依名稱的 DLL 匯出函式](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。

> [!NOTE]
>  當將 DLL 原始程式碼從 win16 移植到 Win32，取代每個執行個體 **__export**具有 **__declspec （dllexport)**。

做為參考，搜尋整個 Win32 Winbase.h 標頭檔。 它包含的範例 **__declspec （dllimport)** 使用量。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [使用.def 檔從 DLL 匯出](exporting-from-a-dll-using-def-files.md)

- [匯出和匯入使用 AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [匯出 c + + 函式，以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [匯出 C 函式，以用於 C 或 c + + 語言可執行檔](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [將應用程式使用 __declspec （dllimport） 匯入](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [__Declspec 關鍵字](../cpp/declspec.md)

- [匯入和匯出內嵌函式](importing-and-exporting-inline-functions.md)

- [交互匯入](mutual-imports.md)

## <a name="see-also"></a>另請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
