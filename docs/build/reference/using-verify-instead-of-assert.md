---
title: 使用 VERIFY 取代 ASSERT
ms.date: 11/04/2016
f1_keywords:
- assert
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: 9ec1a763df6fcf2a1fffe4cb956076d2c7557cb5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412610"
---
# <a name="using-verify-instead-of-assert"></a>使用 VERIFY 取代 ASSERT

假設當您執行偵錯版本的 MFC 應用程式時，沒有任何問題。 不過，相同的應用程式的發行版本損毀，會傳回不正確的結果，及/或表現出某些其他異常行為。

當您將重要的程式碼中的判斷提示陳述式，來確認正確執行，可能被造成這個問題。 ASSERT 陳述式標記為註解 MFC 程式的發行組建中，因為程式碼就不會執行在發行組建。

如果您使用判斷提示來確認函式呼叫成功，請考慮使用[確認](../../mfc/reference/diagnostic-services.md#verify)改。 VERIFY 巨集評估自己的引數，在這兩個偵錯和發行組建的應用程式。

另一個慣用的技術是將函式的傳回值指派給暫存變數，並接著測試判斷提示陳述式中的 變數。

檢查下列程式碼片段：

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

在 偵錯版本的 MFC 應用程式完全執行此程式碼。 如果呼叫`calloc( )`失敗，會顯示診斷訊息，其中包含的檔案和行號。 不過，在 MFC 應用程式的零售組建中：

- 若要在呼叫`calloc( )`絕不會發生，離開`buf`未初始化，或

- `strcpy_s( )` 複製 「`Hello, World`」 到隨機的一種記憶體，可能會使應用程式或導致系統停止回應，或

- `free()` 嘗試釋放從未配置的記憶體。

若要正確使用判斷提示，此程式碼範例應該變更為下列：

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
