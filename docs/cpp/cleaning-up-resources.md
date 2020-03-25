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
ms.openlocfilehash: ba7841f4fa8f0b6654e78e529e82f86237707787
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180859"
---
# <a name="cleaning-up-resources"></a>清除資源

在終止處理常式執行期間，您可能不知道在呼叫終止處理常式之前實際配置了哪些資源。 **__Try**語句區塊可能會在配置所有資源之前中斷，因此不會開啟所有資源。

因此，為了安全起見，您應該先檢查哪些資源已實際開啟，再繼續進行終止處理的清除作業。 建議的程序是：

1. 將控制代碼初始化為 NULL。

1. 在 **__try**語句區塊中，配置資源。 資源一配置，控制代碼就會設定為正值。

1. 在 **__finally**語句區塊中，釋放對應的控制碼或旗標變數為非零或非 Null 的每個資源。

## <a name="example"></a>範例

例如，下列程式碼會使用終止處理常式關閉三個檔案，以及在 **__try**語句區塊中配置的記憶體區塊。 在清除資源之前，程式碼會先檢查資源是否已配置。

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

## <a name="see-also"></a>另請參閱

[撰寫終止處理常式](../cpp/writing-a-termination-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
