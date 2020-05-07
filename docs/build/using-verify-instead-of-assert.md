---
title: 使用 VERIFY 取代 ASSERT
ms.date: 05/06/2019
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: bfc0847677ae232fef67ab6200c626472f042bdb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438617"
---
# <a name="using-verify-instead-of-assert"></a>使用 VERIFY 取代 ASSERT

假設當您執行 MFC 應用程式的 debug 版本時，沒有任何問題。 不過，相同應用程式的發行版本會損毀、傳回不正確的結果，以及（或）展示一些其他異常行為。

當您將重要的程式碼放在 ASSERT 語句中，以確認它是否正確執行時，可能會造成此問題。 由於在 MFC 程式的發行組建中，ASSERT 語句會加上批註，因此程式碼不會在發行組建中執行。

如果您要使用判斷提示來確認函式呼叫是否成功，請考慮改為使用 [[驗證](../mfc/reference/diagnostic-services.md#verify)]。 VERIFY 宏會在應用程式的 [debug] 和 [release] 組建中，評估它自己的引數。

另一個慣用的方法是將函數的傳回值指派給暫存變數，然後在 ASSERT 語句中測試變數。

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

這段程式碼會在 MFC 應用程式的 debug 版本中順利執行。 如果呼叫`calloc( )`失敗，則會顯示包含檔案和行號的診斷訊息。 不過，在 MFC 應用程式的零售組建中：

- `calloc( )`永遠不會呼叫，而會`buf`保留未初始化，或

- `strcpy_s( )`將 "`Hello, World`" 複製到隨機的記憶體片段中，可能會使應用程式損毀或造成系統停止回應，或

- `free()`嘗試釋放從未配置的記憶體。

若要正確使用 ASSERT，程式碼範例應變更為下列內容：

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

或者，您可以改為使用 [驗證]：

```
enum {
    sizeOfBuffer = 20
};
char *buf;
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

## <a name="see-also"></a>請參閱

[解決發行組建的問題](fixing-release-build-problems.md)
