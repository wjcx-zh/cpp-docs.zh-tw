---
title: setjmp longjump
ms.date: 11/04/2016
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
ms.openlocfilehash: 765cef3f02bed09bed0278aaeecdcdbd55d86b67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427894"
---
# <a name="setjmplongjump"></a>setjmp/longjump

當您包含 setjmpex.h 或 setjmp.h 時，所有呼叫[setjmp](../c-runtime-library/reference/setjmp.md)或是[longjmp](../c-runtime-library/reference/longjmp.md)回溯會叫用解構函式，最後會呼叫將會導致。  這不同於 x86，其中包括 setjmp.h 結果在 finally 子句和解構函式不被叫用所示。

呼叫`setjmp`會保留目前的堆疊指標、 非靜態暫存器中，與 MxCsr 暫存器。  若要呼叫`longjmp`返回最近`setjmp`呼叫站台和重設堆疊指標、 靜態暫存器和 MxCsr 暫存器，為狀態為保留的最新`setjmp`呼叫。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../build/calling-convention.md)