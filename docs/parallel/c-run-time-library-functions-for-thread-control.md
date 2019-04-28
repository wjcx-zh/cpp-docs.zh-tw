---
title: 執行緒控制的 C 執行階段程式庫函式
ms.date: 11/04/2016
helpviewer_keywords:
- _beginthread function
- _endthread function
- threading [C++], controlling threads
- multithreading [C++], controlling threads
- _beginthreadex function
- _endthreadex function
ms.assetid: 39d0529c-c392-4c6f-94f5-105d1e8054e4
ms.openlocfilehash: 392fc8e842d86a17013502ffc68c89eb65ba23db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236669"
---
# <a name="c-run-time-library-functions-for-thread-control"></a>執行緒控制的 C 執行階段程式庫函式

所有 Win32 程式都必須至少一個執行緒。 任何執行緒可以建立額外的執行緒。 執行緒可以快速地完成其工作，然後終止，或可以保持使用中程式的存留期間。

嵌入 LIBCMT 和 MSVCRT C 執行階段程式庫提供下列函式的執行緒建立和終止： [_beginthread、 _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)並[_endthread、 _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)。

`_beginthread`和`_beginthreadex`函式會建立新的執行緒，並傳回執行緒識別項，如果作業成功。 如果它在完成執行時，或它可以將自動終止呼叫的執行緒終止自動`_endthread`或`_endthreadex`。

> [!NOTE]
> 如果您要從使用 Libcmt.lib 建置的程式中呼叫 C 執行階段常式，您必須先啟動您使用的執行緒`_beginthread`或`_beginthreadex`函式。 請勿使用 Win32 函式`ExitThread`和`CreateThread`。 使用`SuspendThread`時可能會導致死結多個執行緒遭到封鎖而等待 暫止的執行緒完成其存取權的 C 執行階段資料結構。

##  <a name="_core_the__beginthread_function"></a> _Beginthread 和 _beginthreadex 函式

`_beginthread`和`_beginthreadex`函式會建立新的執行緒。 執行緒與處理程序中的其他執行緒共用的程式碼和資料區段的處理程序，但是有它自己的唯一暫存器值、 堆疊空間和目前的指令位址。 系統會提供 CPU 時間的每個執行緒，好讓處理程序中的所有執行緒可以同時都執行。

`_beginthread` 並`_beginthreadex`類似於[CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) Win32 API 中的函式但有下列差異：

- 它們會初始化特定 C 執行階段程式庫變數。 這很重要，只有當您使用 C 執行階段程式庫中您的執行緒。

- `CreateThread` 有助於讓您控制安全性屬性。 您可以使用此函式，以啟動在暫停狀態的執行緒。

`_beginthread` 和`_beginthreadex`傳回至新的執行緒如果成功則為錯誤碼的控制代碼，如果發生錯誤。

##  <a name="_core_the__endthread_function"></a> _Endthread 和 _endthreadex 函式

[_Endthread](../c-runtime-library/reference/endthread-endthreadex.md)函式會終止所建立的執行緒`_beginthread`(同樣地，`_endthreadex`終止所建立的執行緒`_beginthreadex`)。 執行緒會自動終止何時完成。 `_endthread` 和`_endthreadex`可用於從執行緒內的條件式終止。 比方說，如果無法取得控制項的通訊埠的可以結束執行緒專門用來處理的通訊。

## <a name="see-also"></a>另請參閱

[使用 C 和 Win32 進行多執行緒處理](multithreading-with-c-and-win32.md)
