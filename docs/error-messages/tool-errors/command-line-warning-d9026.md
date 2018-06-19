---
title: 命令列警告 D9026 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2d99573ee46c51178cc2fe995fa0f526b800f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299834"
---
# <a name="command-line-warning-d9026"></a>命令列警告 D9026
選項會套用到整個命令列  
  
 指定的檔名之後命令上指定的選項。 選項已套用到在其前方的檔案。  
  
 例如，在命令  
  
```  
CL verdi.c /G5 puccini.c  
```  
  
 檔案 /g4 將使用不 /g4 是預設的 /G5 選項進行編譯。  
  
 此行為是不同的一些先前的版本，才指定檔名，導致 /g4 之前的選項編譯/G4 和而 puccini.c 會以編譯 /G5 套用。