---
title: 經過時間：一般用途類別
ms.date: 11/04/2016
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating
- elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
ms.openlocfilehash: 5990f6f5db0270c8d24ff35b5c9bbea5b24e6ed7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236270"
---
# <a name="elapsed-time-general-purpose-classes"></a>經過時間：一般用途類別

下列程序示範如何計算兩個之間的差異`CTime`物件，以及如何取得`CTimeSpan`結果。 使用`CTime`和`CTimeSpan`物件來計算經過的時間，如下所示：

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

一旦您已計算`elapsedTime`，您可以使用的成員函式`CTimeSpan`擷取的經過時間值的元件。
