---
title: 匯出 |Microsoft Docs
ms.custom: ''
ms.date: 08/20/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- EXPORTS
dev_langs:
- C++
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 299d300cb3b2247a4dfa698a53c486bcef6164e3
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894547"
---
# <a name="exports"></a>EXPORTS

引入一個或多個匯出定義的區段，以指定函式或資料的已匯出名稱或序數。 每一個定義都必須在不同的行上。

```DEF
EXPORTS
   definition
```  

## <a name="remarks"></a>備註

第一個*定義*可以在同一行上`EXPORTS`關鍵字或後續的行上。 .DEF 檔可以包含一個或多個 `EXPORTS` 陳述式。

匯出的語法*定義*是：

```DEF
entryname[=internal_name|other_module.another_exported_name] [@Ordinal [NONAME]] [[PRIVATE] | [DATA]]
```

*entryname*是您想要匯出的函式或變數名稱。 此為必要項。 如果您將匯出的名稱與 DLL 中的名稱不同，在 DLL 中指定匯出的名稱使用*internal_name*。 例如，如果您的 DLL 匯出函式 `func1`，且您想要呼叫端使用它作為 `func2`，則您可以指定：

```DEF
EXPORTS
   func2=func1
```

如果您將匯出的名稱，從某些其他模組匯出的名稱在 DLL 中使用指定*other_module.exported_name*。 例如，如果您的 DLL 匯出函式 `other_module.func1`，且您想要呼叫端使用它作為 `func2`，則您可以指定：

```DEF
EXPORTS
   func2=other_module.func1
```

如果您將匯出的名稱是從另一個模組中，依序數匯出，請指定 使用匯出的 DLL 中的序數*other_module。 #ordinal_number*。 例如，如果您的 DLL 匯出函式，從另一個模組是序數 42，而您想要使用它作為呼叫者`func2`，您就要指定：

```DEF
EXPORTS
   func2=other_module.#42
```

因為 Visual c + + 編譯器會使用 c + + 函式的名稱裝飾，所以您必須使用裝飾的名稱 internal_name，或使用 extern"C"中的原始程式碼定義匯出的函式。 編譯器也會裝飾使用的 C 函式[__stdcall](../../cpp/stdcall.md)呼叫慣例以底線 (\_) 前置詞和後置詞組成 at 符號 (\@) 後面中的位元組數 （十進位）引數清單。

若要尋找由編譯器所產生的裝飾的名稱，請使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具或連結器[/typedefs/ 對應](../../build/reference/map-generate-mapfile.md)選項。 裝飾名稱是編譯器專屬的。 如果您匯出 .DEF 檔案中的裝飾名稱，則連結至 DLl 的可執行檔必須也使用相同版本的編譯器進行建置。 這可確保呼叫端的裝飾名稱符合 .DEF 檔案中的已匯出名稱。

您可以使用\@*序數*指定數字，而不是函式名稱，將會進入 DLL 的匯出表。 許多 Windows DLL 會匯出序數，以支援舊版程式碼。 通常在 16 位元 Windows 程式碼中使用序數，因為它有助於最大程度減小 DLL 的大小。 建議除非您的 DLL 用戶端因舊版支援而需要序數，否則不要依序數匯出函式。 由於 .LIB 檔會包含序數與函式之間的對應，因此您可以像在使用 DLL 的專案中那樣，使用函式名稱。

使用選擇性**NONAME**關鍵字，您可以僅依序數匯出，並減少產生的 DLL 中匯出表格的大小。 不過，如果您想要使用[GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) DLL 時，在您必須了解序數，因為名稱不是有效。

選擇性的關鍵字**私人**可防止*entryname*以免包含在 LINK 所產生的匯入程式庫。 她不會影響也由 LINK 產生之映像檔中的匯出。

選擇性的關鍵字**資料**指定匯出為資料，而不是程式碼。 此範例顯示您可以如何匯出名為 `exported_global` 的資料變數：

```DEF
EXPORTS
   exported_global DATA
```  

有四種方法匯出定義，按建議順序列出：

1. [__Declspec （dllexport)](../../cpp/dllexport-dllimport.md)原始程式碼中的關鍵字

2. .DEF 檔中的 `EXPORTS` 陳述式

3. [/匯出](../../build/reference/export-exports-a-function.md)LINK 命令中的規格

4. A[註解](../../preprocessor/comment-c-cpp.md)在原始程式碼中，表單的指示詞 `#pragma comment(linker, "/export: definition ")`  

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

[模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)
