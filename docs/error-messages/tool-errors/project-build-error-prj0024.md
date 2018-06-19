---
title: 專案建置錯誤 PRJ0024 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59bf76aba80093bf9e8e653bdfb9fad49687a501
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318343"
---
# <a name="project-build-error-prj0024"></a>專案建置錯誤 PRJ0024
Unicode 路徑 'path' 無法轉譯為使用者 ANSI 字碼頁。  
  
 ***路徑***是原始的 Unicode 版本的路徑字串。 這個錯誤可能的情況下是無法直接轉譯為 ANSI 目前的系統字碼頁的 Unicode 路徑。  
  
 如果您正在使用所開發的專案上使用字碼頁不在您的電腦上的系統，可能會發生這個錯誤。  
  
 此錯誤的解決方法是，更新來使用 ANSI 文字，或在電腦上安裝的字碼頁，並將它設定為系統預設值的路徑。