---
title: 專案建置警告 PRJ0041 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0041
dev_langs:
- C++
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7677c5718783065f64e52f98f7ddbed76e905d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038135"
---
# <a name="project-build-warning-prj0041"></a>專案建置警告 PRJ0041

找不到遺失依存性的檔案 'file' 的 「 相依性 」。 您的專案仍會建置，但可能會繼續顯示為過期，直到找到這個檔案。

檔案 （資源檔或.idl/.odl 檔案，例如包含專案系統無法解析的 include 陳述式。

由於專案系統不會處理前置處理器陳述式 (例如 #if)，產生錯誤的陳述式實際上可能不是組建的一部分。

若要解決這個警告，刪除在.rc 檔中所有不必要的程式碼，或加入的適當名稱的預留位置檔案。