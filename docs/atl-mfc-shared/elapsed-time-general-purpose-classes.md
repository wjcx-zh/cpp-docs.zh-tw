---
title: 經過時間： 一般用途類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff07c1b26649ffd591bcab9917cf45fa4c67f30a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756512"
---
# <a name="elapsed-time-general-purpose-classes"></a>經過時間： 一般用途類別

下列程序示範如何計算兩個之間的差異`CTime`物件，以及如何取得`CTimeSpan`結果。 使用`CTime`和`CTimeSpan`物件來計算經過的時間，如下所示：

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

一旦您已計算`elapsedTime`，您可以使用的成員函式`CTimeSpan`擷取的經過時間值的元件。  

