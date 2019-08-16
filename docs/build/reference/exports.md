---
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 8338f27d35d3779a55b83b70c7a3eef285a91f46
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492889"
---
# <a name="exports"></a>EXPORTS

引入一個或多個匯出定義的區段，以指定函式或資料的已匯出名稱或序數。 每一個定義都必須在不同的行上。

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>備註

第一個*定義*可以位於與`EXPORTS`關鍵字相同的行上, 或在後續的一行。 .DEF 檔可以包含一個或多個 `EXPORTS` 陳述式。

匯出*定義*的語法如下:

> *entryname* *internal_name other_module. exported_name*]序數\[ **NONAME]** ] \[ **\@** | \[ __=__ \[ \[**私**用]|**DATA]** ] \[

*entryname*是您想要匯出的函式或變數名稱。 此為必要項。 如果您匯出的名稱與 DLL 中的名稱不同, 請使用*internal_name*, 在 dll 中指定匯出的名稱。 例如，如果您的 DLL 匯出函式 `func1`，且您想要呼叫端使用它作為 `func2`，則您可以指定：

```DEF
EXPORTS
   func2=func1
```

如果您匯出的名稱來自某個其他模組, 請使用*other_module*, 在 DLL 中指定匯出的名稱。 例如，如果您的 DLL 匯出函式 `other_module.func1`，且您想要呼叫端使用它作為 `func2`，則您可以指定：

```DEF
EXPORTS
   func2=other_module.func1
```

如果您匯出的名稱來自于依序數匯出的另一個模組, 請使用*other_module*, 在 DLL 中指定匯出的序數。 __#__ *序數*。 例如, 如果您的 DLL 從另一個模組 (其為序數 42) 匯出函式, 而您想要讓呼叫者`func2`使用它做為, 您可以指定:

```DEF
EXPORTS
   func2=other_module.#42
```

因為 MSVC 編譯器會針對C++函式使用名稱裝飾, 所以您必須使用裝飾名稱*internal_name* , 或在原始程式碼中使用`extern "C"`來定義匯出的函式。 編譯器也會裝飾使用[__stdcall](../../cpp/stdcall.md)呼叫慣例的 C 函式, 加上底線\_() 前置詞, 以及由 @ 符號 (\@) 組成的後置詞, 後面接著引數清單中的位元組數目 (以十進位為單位)。

若要尋找編譯器所產生的裝飾名稱, 請使用[DUMPBIN](dumpbin-reference.md)工具或連結器[/MAP](map-generate-mapfile.md)選項。 裝飾名稱是編譯器專屬的。 如果您匯出 .DEF 檔案中的裝飾名稱，則連結至 DLl 的可執行檔必須也使用相同版本的編譯器進行建置。 這可確保呼叫端的裝飾名稱符合 .DEF 檔案中的已匯出名稱。

您可以使用\@*序數*來指定某個數位 (而不是函數名稱) 進入 DLL 的匯出資料表。 許多 Windows DLL 會匯出序數，以支援舊版程式碼。 通常在 16 位元 Windows 程式碼中使用序數，因為它有助於最大程度減小 DLL 的大小。 建議除非您的 DLL 用戶端因舊版支援而需要序數，否則不要依序數匯出函式。 由於 .LIB 檔會包含序數與函式之間的對應，因此您可以像在使用 DLL 的專案中那樣，使用函式名稱。

藉由使用選擇性的**NONAME**關鍵字, 您只可以依序數匯出, 並減少產生之 DLL 中的匯出資料表大小。 不過, 如果您想要在 DLL 上使用[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) , 就必須知道序數, 因為名稱將無效。

選擇性關鍵字**PRI加值稅E**可防止*entryname*包含在連結所產生的匯入程式庫中。 她不會影響也由 LINK 產生之映像檔中的匯出。

選擇性關鍵字**資料**會指定匯出是資料, 而非程式碼。 此範例顯示您可以如何匯出名為 `exported_global` 的資料變數：

```DEF
EXPORTS
   exported_global DATA
```

有四種方法匯出定義，按建議順序列出：

1. 原始程式碼中的[__declspec (dllexport)](../../cpp/dllexport-dllimport.md)關鍵字

1. .DEF 檔中的 `EXPORTS` 陳述式

1. 連結命令中的[/export](export-exports-a-function.md)規格

1. 原始程式碼中的[批註](../../preprocessor/comment-c-cpp.md)指示詞, 格式`#pragma comment(linker, "/export: definition ")`為。 下列範例顯示函式宣告之前的 #pragma comment 指示詞, 其中`PlainFuncName`是未修飾的名稱, 而`_PlainFuncName@4`是函式的裝飾名稱:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

如果您需要匯出未修飾函式名稱, 而且根據組建設定 (例如, 在32位或64位組建中) 有不同的匯出, 則 #pragma 指示詞很有用。

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
