---
title: 清除資源
description: 如何在結構化例外狀況處理的終止處理常式期間釋放資源。
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
ms.openlocfilehash: dae92a515db25b9985a890d7d08cc213f88ecfea
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898437"
---
# <a name="cleaning-up-resources"></a>清除資源

在終止處理常式執行期間，您可能不知道在呼叫終止處理常式之前，已取得了哪些資源。 在 **`__try`** 取得所有資源之前，語句區塊可能會中斷，因此不會開啟所有資源。

為了安全起見，您應該先查看哪些資源已開啟，然後再繼續進行終止處理清除。 建議的程序是：

1. 將控制代碼初始化為 NULL。

1. 在 **`__try`** 語句區塊中，取得資源。 當取得資源時，控制碼會設定為正值。

1. 在 **`__finally`** 語句區塊中，釋放相對應的控制碼或旗標變數為非零或非 Null 的每個資源。

## <a name="example"></a>範例

例如，下列程式碼會使用終止處理常式來關閉三個檔案並釋放記憶體區塊。 這些資源是在 **`__try`** 語句區塊中取得。 清除資源之前，程式碼會先檢查是否已取得資源。

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

[撰寫終止處理常式](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
