---
title: "專案建置警告 PRJ0041 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0041
dev_langs: C++
helpviewer_keywords: PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 231b58cb0c13d1a3f87e010a5100da564b0be806
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-warning-prj0041"></a>專案建置警告 PRJ0041
找不到遺漏相依性的檔案 'file' 的 ' 相依性'。 您的專案仍會建置，但可能會繼續顯示為過期，直到找到這個檔案。  
  
 檔案 （資源檔或.idl/.odl 檔案，例如包含專案系統無法解析的 include 陳述式。  
  
 由於專案系統不會處理前置處理器陳述式 (例如 #if)，產生錯誤的陳述式實際上可能不是組建的一部分。  
  
 若要解決這個警告，刪除在.rc 檔中所有不必要的程式碼或加入適當名稱的預留位置檔案。