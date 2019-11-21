---
title: 清除資源
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
ms.openlocfilehash: 225c3ccaf3342f11ad4eb6d6575ad3ac542acfd2
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246640"
---
# <a name="cleaning-up-resources"></a>清除資源

在終止處理常式執行期間，您可能不知道在呼叫終止處理常式之前實際配置了哪些資源。 It is possible that the **__try** statement block was interrupted before all resources were allocated, so that not all resources were opened.

因此，為了安全起見，您應該先檢查哪些資源已實際開啟，再繼續進行終止處理的清除作業。 建議的程序是：

1. 將控制代碼初始化為 NULL。

1. In the **__try** statement block, allocate resources. 資源一配置，控制代碼就會設定為正值。

1. In the **__finally** statement block, release each resource whose corresponding handle or flag variable is nonzero or not NULL.

## <a name="example"></a>範例

For example, the following code uses a termination handler to close three files and a memory block that were allocated in the **__try** statement block. 在清除資源之前，程式碼會先檢查資源是否已配置。

```cpp
// exceptions_Cleaning_up_Resources.cpp
#include <stdlib.h>
#include <malloc.h>
#include <stdio.h>
#include <windows.h>

void fileOps() {
   FILE  *fp1 = NULL,
         *fp2 = NULL,
         *fp3 = NULL;
   LPVOID lpvoid = NULL;
   errno_t err;

   __try {
      lpvoid = malloc( BUFSIZ );

      err = fopen_s(&fp1, "ADDRESS.DAT", "w+" );
      err = fopen_s(&fp2, "NAMES.DAT", "w+" );
      err = fopen_s(&fp3, "CARS.DAT", "w+" );
   }
   __finally {
      if ( fp1 )
         fclose( fp1 );
      if ( fp2 )
         fclose( fp2 );
      if ( fp3 )
         fclose( fp3 );
      if ( lpvoid )
         free( lpvoid );
   }
}

int main() {
   fileOps();
}
```

## <a name="see-also"></a>請參閱

[Writing a termination handler](../cpp/writing-a-termination-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)