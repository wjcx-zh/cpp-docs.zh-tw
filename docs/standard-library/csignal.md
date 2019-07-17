---
title: '&lt;csignal&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csignal>
helpviewer_keywords:
- csignal header
ms.assetid: d18bcf82-a89a-476c-a6bf-726af956f7c0
ms.openlocfilehash: 298aa14c4e41f1473cac72fc79aa3e180dfe183f
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243564"
---
# <a name="ltcsignalgt"></a>&lt;csignal&gt;

包含標準 C 程式庫標頭\<signal.h >，並將關聯的名稱加入`std`命名空間。 包含此標頭可保證，透過使用 Standard C 程式庫標頭中的外部連結所宣告的名稱會在 `std` 命名空間中宣告。


## <a name="syntax"></a>語法

```cpp
#include <csignal>
```

## <a name="namespace-and-macros"></a>命名空間和巨集

```cpp
namespace std {
    using sig_atomic_t = see below;

    extern using signal-handler = void(int);
}

#define SIG_DFL
#define SIG_ERR
#define SIG_IGN
#define SIGABRT
#define SIGFPE
#define SIGILL
#define SIGINT
#define SIGSEGV
#define SIGTERM
```

## <a name="functions"></a>函式

```cpp
signal-handler* signal(int sig, signal-handler* func);
int raise(int sig);
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
