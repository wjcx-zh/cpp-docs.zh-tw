---
title: "匯出 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EXPORTS
dev_langs:
- C++
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f9a8e902e42d44ffa292b9f821839b8e948d7a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exports"></a>EXPORTS
引入一個或多個匯出定義的區段，以指定函式或資料的已匯出名稱或序數。 每一個定義都必須在不同的行上。  
  
```  
EXPORTS  
   definition  
```  
  
## <a name="remarks"></a>備註  
 第一個 `definition` 可以位於與 `EXPORTS` 關鍵字相同的行上，或者位於後續行上。 .DEF 檔可以包含一個或多個 `EXPORTS` 陳述式。  
  
 匯出 `definition` 的語法是：  
  
```  
  
entryname[=internalname] [@ordinal [NONAME]] [[PRIVATE] | [DATA]]  
```  
  
 `entryname` 是您要匯出的函式或變數名稱。 此為必要項。 如果您匯出的名稱與 DLL 中的名稱不同，請使用 `internalname`，在 DLL 中指定匯出的名稱。 例如，如果您的 DLL 匯出函式 `func1`，且您想要呼叫端使用它作為 `func2`，則您可以指定：  
  
```  
EXPORTS  
   func2=func1  
```  
  
 因為 Visual C++ 編譯器對 ++ 函式使用名稱裝飾，所以您必須使用裝飾名稱作為 `entryname` 或 `internalname`，或者在原始程式碼中使用 `extern "C"` 定義匯出的函式。 編譯器還會裝飾使用的 C 函式[__stdcall](../../cpp/stdcall.md)呼叫慣例以底線 (_) 為前置和後置詞組成 at 符號 (@) 後面接著位元組數 （十進位） 引數清單中。  
  
 若要尋找編譯器產生的裝飾的名稱，請使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具或連結器[對應](../../build/reference/map-generate-mapfile.md)選項。 裝飾名稱是編譯器專屬的。 如果您匯出 .DEF 檔案中的裝飾名稱，則連結至 DLl 的可執行檔必須也使用相同版本的編譯器進行建置。 這可確保呼叫端的裝飾名稱符合 .DEF 檔案中的已匯出名稱。  
  
 您可以使用 @`ordinal`，來指定號碼而非函式名稱將進入 DLL 的匯出表格。 許多 Windows DLL 會匯出序數，以支援舊版程式碼。 通常在 16 位元 Windows 程式碼中使用序數，因為它有助於最大程度減小 DLL 的大小。 建議除非您的 DLL 用戶端因舊版支援而需要序數，否則不要依序數匯出函式。 由於 .LIB 檔會包含序數與函式之間的對應，因此您可以像在使用 DLL 的專案中那樣，使用函式名稱。  
  
 透過使用選用的 `NONAME` 關鍵字，您可以僅依序數匯出，並減少所產生 DLL 中匯出表格的大小。 不過，如果您想要使用[GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)上 DLL 時，您必須了解序數，因為名稱不是有效。  
  
 選用關鍵字 `PRIVATE` 會防止 `entryname` 包含在 LINK 所產生的匯入程式庫中。 她不會影響也由 LINK 產生之映像檔中的匯出。  
  
 選用關鍵字 `DATA` 會指定匯出是資料，不是程式碼。 此範例顯示您可以如何匯出名為 `exported_global` 的資料變數：  
  
```  
EXPORTS  
   exported_global DATA  
```  
  
 有四種方法匯出定義，按建議順序列出：  
  
1.  [__Declspec （dllexport)](../../cpp/dllexport-dllimport.md)的原始程式碼中的關鍵字  
  
2.  .DEF 檔中的 `EXPORTS` 陳述式  
  
3.  [/EXPORT](../../build/reference/export-exports-a-function.md) LINK 命令中的規格  
  
4.  A[註解](../../preprocessor/comment-c-cpp.md)在原始程式碼中，表單的指示詞`#pragma comment(linker, "/export: definition ")`  
  
 所有四種方法可在同一程式中使用。 當 LINK 繫結的程式包含匯出時，它還會建立匯入程式庫，除非組建中使用 .EXP 檔。  
  
 EXPORTS 區段的範例如下：  
  
```  
EXPORTS  
   DllCanUnloadNow      @1          PRIVATE  
   DllWindowName = WindowName       DATA  
   DllGetClassObject    @4 NONAME   PRIVATE  
   DllRegisterServer    @7  
   DllUnregisterServer  
```  
  
 當您使用 .DEF 檔從 DLL 匯出變數時，您無需在變數上指定 `__declspec(dllexport)`。 不過，在使用 DLL 的任何檔案中，您必須在資料的宣告上，仍使用 `__declspec(dllimport)`。  
  
## <a name="see-also"></a>請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)