---
title: "命令列警告 D9026 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9127ad1887d476e5460798f806c2db1ff3144de3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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