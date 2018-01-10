---
title: "CL 選項的順序 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cl
dev_langs: C++
helpviewer_keywords: cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ef67792b01d4d4dab535bfb180cd70beb2316b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="order-of-cl-options"></a>CL 選項的順序
選項可以出現的任何位置上 CL 命令列中，除了 /link 選項，它必須出現在上一次。 編譯器選項中指定的開頭[CL 環境變數](../../build/reference/cl-environment-variables.md)，然後讀取命令列從左到右 — 處理遇到它們的順序的命令檔。 每個選項會套用至命令列上的所有檔案。 如果 CL 發生衝突的選項，它會使用最右邊的選項。  
  
## <a name="see-also"></a>請參閱  
 [編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)