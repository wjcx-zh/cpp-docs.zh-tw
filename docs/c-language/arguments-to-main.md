---
title: main 的引數
ms.date: 11/04/2016
ms.assetid: 39824fef-05ad-461d-ae82-49447dda8060
ms.openlocfilehash: 918be9d281f1cb12c27c6c2f5dd834e4af137179
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313554"
---
# <a name="arguments-to-main"></a>main 的引數

**ANSI 2.1.2.2.1**：main 的引數語意

在 Microsoft C 中，在程式啟動時呼叫的函式稱為 **main**。 不會針對 **main** 宣告原型，因此可以為它定義零個、兩個或三個參數：

```
int main( void )
int main( int argc, char *argv[] )
int main( int argc, char *argv[], char *envp[] )
```

上面的第三行中 **main** 會接受三個參數，該行是 ANSI C 標準的 Microsoft 延伸模組。 第三個參數 **envp** 是環境變數的指標陣列。 **envp** 陣列是以 null 指標終止。 如需 **main** 和 **envp** 的詳細資訊，請參閱[執行 main 函式和程式](../c-language/main-function-and-program-execution.md)。

變數 **argc** 絕不會保留負值。

包含 null 指標的字串陣列是以 **argv[argc]** 結尾。

**argv** 陣列的所有項目都是字串指標。

未使用命令列引數叫用的程式將收到值為 1 的 **argc**，而可執行檔的名稱會放入 **argv[0]** 中 (在 MS-DOS 3.0 以前的版本中，無法使用可執行檔名稱。 字母 "C" 會放在**argv [0]** 中）。**Argv [1]** 透過**argv [argc-1]** 所指向的字串代表程式參數。

**argc** 和 **argv** 參數可修改，並且會保留在程式啟動和程式終止之間最後儲存的值。

## <a name="see-also"></a>請參閱

[環境](../c-language/environment.md)
