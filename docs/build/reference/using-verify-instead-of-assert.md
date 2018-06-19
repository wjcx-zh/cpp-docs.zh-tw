---
title: 使用 VERIFY 取代 ASSERT |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- assert
dev_langs:
- C++
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 712c22bec1d6ce2d67208de9a139dff7621ad4cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376555"
---
# <a name="using-verify-instead-of-assert"></a>使用 VERIFY 取代 ASSERT
假設，當您執行 MFC 應用程式的偵錯版本，不會發生問題。 不過，相同的應用程式的發行版本發生當機、 傳回不正確的結果，及/或展示其他異常的行為。  
  
 當您將重要的程式碼放在 ASSERT 陳述式來確認正確執行，可能被造成這個問題。 ASSERT 陳述式標記為註解中的 MFC 程式的發行組建，因為程式碼不會在發行組建中執行。  
  
 如果您使用判斷提示來確認函式呼叫成功，請考慮使用[確認](../../mfc/reference/diagnostic-services.md#verify)改為。 VERIFY 巨集評估自己的引數，在這兩個偵錯和發行組建的應用程式。  
  
 另一個建議方法是將函式的傳回值指派給暫存變數，然後在 ASSERT 陳述式中測試變數中。  
  
 檢查有下列的程式碼片段：  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 此程式碼偵錯版本的 MFC 應用程式中執行無誤。 如果呼叫`calloc( )`失敗，會顯示包含的檔案和行號的診斷訊息。 不過，在 MFC 應用程式的零售組建中：  
  
-   若要呼叫`calloc( )`絕不會發生，離開`buf`未初始化，或  
  
-   `strcpy_s( )` 複製"`Hello, World`"編入隨機的記憶體，可能會使應用程式或造成系統停止回應，或  
  
-   `free()` 嘗試釋放記憶體永遠不會取消配置。  
  
 正確使用判斷提示，您應該變更程式碼範例，以下列：  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );  
ASSERT( buf != NULL );  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 或者，您可以改為使用驗證：  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
## <a name="see-also"></a>另請參閱  
 [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)