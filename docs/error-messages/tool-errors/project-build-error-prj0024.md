---
title: "專案建置錯誤 PRJ0024 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2cf9ad974856f132599932a32b954e50453adf56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0024"></a>專案建置錯誤 PRJ0024
Unicode 路徑 'path' 無法轉譯為使用者 ANSI 字碼頁。  
  
 ***路徑***是原始的 Unicode 版本的路徑字串。 這個錯誤可能的情況下是無法直接轉譯為 ANSI 目前的系統字碼頁的 Unicode 路徑。  
  
 如果您正在使用所開發的專案上使用字碼頁不在您的電腦上的系統，可能會發生這個錯誤。  
  
 此錯誤的解決方法是，更新來使用 ANSI 文字，或在電腦上安裝的字碼頁，並將它設定為系統預設值的路徑。