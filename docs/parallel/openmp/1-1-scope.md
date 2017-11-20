---
title: "1.1 範圍 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b4f348f55cb956802bab9651b22804c941c53cdb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="11-scope"></a>1.1 範圍
此規格涵蓋只有使用者導向平行化作業，其中使用者明確地指定才能以平行方式執行程式的編譯器和執行階段系統所採取的動作。 OpenMP C 和 c + + 實作不需要檢查有相依性、 衝突、 死結、 競爭情形或其他問題，導致不正確的程式執行。 使用者負責確保使用 OpenMP C 和 c + + 應用程式開發介面建構的應用程式會正確執行。 本文件未涵蓋編譯器產生的自動平行處理和編譯器指示詞，以協助這類平行化作業。