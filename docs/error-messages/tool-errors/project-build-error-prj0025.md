---
title: 專案建置錯誤 PRJ0025 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0025
dev_langs:
- C++
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 087a5d5af8ed92bdd0446ae87af037acbfd38a95
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316981"
---
# <a name="project-build-error-prj0025"></a>專案建置錯誤 PRJ0025
批次檔 'file' 包含無法轉譯為使用者 ANSI 字碼頁的 Unicode 內容。  
  
 ***UNICODE 檔案的內容***  
  
 專案系統找到 Unicode 內容中自訂建置規則，或建置無法正確轉譯成使用者的目前 ANSI 字碼頁的事件。  
  
 此錯誤的解決方法是更新的建置規則的內容，或建置事件來使用 ANSI，或是在電腦上安裝的字碼頁，並將它設為系統預設值。  
  
 如需有關自訂建置步驟和建置事件，請參閱[了解自訂建置步驟和建置事件](../../ide/understanding-custom-build-steps-and-build-events.md)。