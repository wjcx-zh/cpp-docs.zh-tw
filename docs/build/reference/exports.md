---
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 9ede0d3b53c975298dea3d1331bc0fb00ac246b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328250"
---
# <a name="exports"></a>EXPORTS

引入一個或多個匯出定義的區段，以指定函式或資料的已匯出名稱或序數。 每一個定義都必須在不同的行上。

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>備註

第一個*定義*`EXPORTS`可以與 關鍵字位於同一行上,也可以位於後續行上。 .DEF 檔可以包含一個或多個 `EXPORTS` 陳述式。

匯出*定義的*語法是:

> *項目名稱*\[__=__*internal_name*\[internal_name **\@** \[ \[ | other_module.exported_name = 二級 NONAME = 私有 | \[ **PRIVATE** _ordinal_ ** ** * *\[**數據**|

*項名稱*是要匯出的函數或變數名稱。 這是必填欄位。 如果匯出的名稱與 DLL 中的名稱不同,請使用*internal_name*在 DLL 中指定匯出的名稱。 例如，如果您的 DLL 匯出函式 `func1`，且您想要呼叫端使用它作為 `func2`，則您可以指定：

```DEF
EXPORTS
   func2=func1
```

如果匯出的名稱來自其他模組,請使用*other_module.exported_name*在 DLL 中指定匯出的名稱。 例如，如果您的 DLL 匯出函式 `other_module.func1`，且您想要呼叫端使用它作為 `func2`，則您可以指定：

```DEF
EXPORTS
   func2=other_module.func1
```

如果匯出的名稱來自由位元匯出的另一個模組,請使用*other_module*在 DLL 中指定匯出的元號。__#__ *ddinal*. 例如,如果 DLL 從具有正項 42 的其他模組匯出函數,並且希望調用`func2`方將其用作 ,則可以指定:

```DEF
EXPORTS
   func2=other_module.#42
```

由於 MSVC 編譯器使用名稱修飾C++函數,因此必須使用修飾名稱*internal_name,*`extern "C"`或者使用原始程式碼 定義匯出的函數。 編譯器還修飾 C 函數,這些函數使用[__stdcall](../../cpp/stdcall.md)調\_用約定,其 前綴和後綴\@由 at sign ( ) 組成,後跟參數清單中的位元數(十進位)。

要查找編譯器生成的修飾名稱,請使用[DUMPBIN](dumpbin-reference.md)工具或連結器[/MAP](map-generate-mapfile.md)選項。 裝飾名稱是編譯器專屬的。 如果您匯出 .DEF 檔案中的裝飾名稱，則連結至 DLl 的可執行檔必須也使用相同版本的編譯器進行建置。 這可確保呼叫端的裝飾名稱符合 .DEF 檔案中的已匯出名稱。

可以使用\@ *ddinal*指定數位(而不是函數名稱)進入 DLL 的匯出表。 許多 Windows DLL 會匯出序數，以支援舊版程式碼。 通常在 16 位元 Windows 程式碼中使用序數，因為它有助於最大程度減小 DLL 的大小。 我們不建議通過元代匯出函數,除非您的 DLL 客戶需要它來提供舊版支援。 由於 .LIB 檔會包含序數與函式之間的對應，因此您可以像在使用 DLL 的專案中那樣，使用函式名稱。

通過使用可選的**NONAME**關鍵字,您只能按位數匯出,並減小生成的 DLL 中的匯出表的大小。 但是,如果要在 DLL 上使用[GetProcAddress,](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)您必須知道序號,因為名稱無效。

可選關鍵字**PRIVATE**可防止*項目名稱*包含在 LINK 生成的導入庫中。 她不會影響也由 LINK 產生之映像檔中的匯出。

可選關鍵字**DATA**指定匯出是數據,而不是代碼。 此範例顯示您可以如何匯出名為 `exported_global` 的資料變數：

```DEF
EXPORTS
   exported_global DATA
```

有四種方法匯出定義，按建議順序列出：

1. 原始碼中的[__declspec(dllexport)](../../cpp/dllexport-dllimport.md)關鍵字

1. .DEF 檔中的 `EXPORTS` 陳述式

1. LINK 指令中的[/EXPORT](export-exports-a-function.md)規範

1. 表單[comment](../../preprocessor/comment-c-cpp.md)`#pragma comment(linker, "/export: definition ")`的註解指令。 下面的範例在函數聲明之前顯示#pragma註釋指令,其中`PlainFuncName`未修飾的名稱`_PlainFuncName@4`是 函數的修飾名稱:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

如果需要匯出未修飾的函數名稱,並且根據生成配置(例如,在 32 位元或 64 位元生成中)具有不同的匯出,則#pragma指令非常有用。

所有四種方法可在同一程式中使用。 當 LINK 繫結的程式包含匯出時，它還會建立匯入程式庫，除非組建中使用 .EXP 檔。

EXPORTS 區段的範例如下：

```DEF
EXPORTS
   DllCanUnloadNow      @1          PRIVATE
   DllWindowName = WindowName       DATA
   DllGetClassObject    @4 NONAME   PRIVATE
   DllRegisterServer    @7
   DllUnregisterServer
```

當您使用 .DEF 檔從 DLL 匯出變數時，您無需在變數上指定 `__declspec(dllexport)`。 不過，在使用 DLL 的任何檔案中，您必須在資料的宣告上，仍使用 `__declspec(dllimport)`。

## <a name="see-also"></a>另請參閱

[模組定義陳述式的規則](rules-for-module-definition-statements.md)
