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

您可以使用 **__declspec(dllexport)** 關鍵字從 DLL 匯出資料、函數、類或類成員函數。 **__declspec(dllexport)** 將匯出指令添加到物件檔,因此無需使用 .def 檔案。

在嘗試匯出修飾C++函數名稱時,這種便利性最為明顯。 由於沒有名稱修飾的標準規範,匯出函數的名稱可能會在編譯器版本之間更改。 如果使用 **__declspec(dllexport),** 則重新編譯 DLL 和從屬 .exe 檔僅需要考慮任何命名約定更改。

許多匯出指令(如指令指令、NONAME 和 PRIVATE)只能在 .def 檔中進行,並且沒有 .def 檔案無法指定這些屬性。 但是,除了使用 .def 檔外,使用 **__declspec(dllexport)** 不會導致生成錯誤。

要匯出函數,如果指定了關鍵字,**則__declspec(dllexport)** 關鍵字必須顯示在調用約定關鍵字的左側。 例如：

```
__declspec(dllexport) void __cdecl Function1(void);
```

要匯出類中的所有公共資料成員和成員函數,關鍵字必須顯示在類名稱的左側,如下所示:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)`不能應用於具有調用約定的`__clrcall`函數。

構建 DLL 時,通常會創建包含要匯出的函數原型和/或類的標頭檔,並將 **__declspec(dllexport)** 添加到標頭檔中的聲明。 要使程式碼更具可讀性,請為 **__declspec(dllexport)** 定義巨集,並將巨集與要匯出的每個符號一起使用:

```
#define DllExport   __declspec( dllexport )
```

**__declspec(dllexport)** 在 DLL 匯出表中儲存函數名稱。 如果要優化表的大小,請參閱[按 Ordinal 而不是按名稱 從 DLL 匯出函數](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [使用 .def 檔案從 DLL 匯出](exporting-from-a-dll-using-def-files.md)

- [使用AFX_EXT_CLASS匯出及匯入](exporting-and-importing-using-afx-ext-class.md)

- [匯出C++函數,用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [匯出 C 函數,用於 C 或 C++語言可執行檔](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [確定要使用的匯出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [__declspec關鍵字](../cpp/declspec.md)

- [匯入和匯出內嵌函式](importing-and-exporting-inline-functions.md)

- [相互進口](mutual-imports.md)

## <a name="see-also"></a>另請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
