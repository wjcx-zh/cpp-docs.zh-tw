---
title: "CL 命令檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cl
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a711b2f4a484a6370af828c5d0aad522686ca3f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cl-command-files"></a>CL 命令檔
命令檔是文字檔，其中包含選項和檔名，否則輸入[命令列](../../build/reference/compiler-command-line-syntax.md)或指定使用[CL 環境變數](../../build/reference/cl-environment-variables.md)。 CL 可以接受做為引數在 CL 環境變數，或在命令列編譯器命令檔。 與命令列或 CL 環境變數不同的是，命令檔可讓您使用多行選項和檔名。  
  
 根據命令檔名稱在 CL 環境變數，或在命令列上的位置來處理選項和命令檔中的檔名。 不過，如果 /link 選項出現在命令檔中，其餘的列上的所有選項都傳遞給連結器。 編譯器選項，仍接受命令檔中的下一行中的選項和命令列上的選項之後的命令檔引動過程。 如需有關選項的順序如何影響其解譯的詳細資訊，請參閱[CL 選項的順序](../../build/reference/order-of-cl-options.md)。  
  
 命令檔不能包含 CL 命令。 每個選項必須開始及結束於同一行;您無法使用反斜線 (\\) 來結合跨兩個線條的選項。  
  
 所指定的命令檔，是 @ 記號 (@) 後面接著 filename;檔案名稱可以指定為絕對或相對路徑。  
  
 例如，如果是名為 回應檔案中的下列命令：  
  
```  
/Og /link LIBC.LIB  
```  
  
 然後指定下列 CL 命令：  
  
```  
CL /Ob2 @RESP MYAPP.C  
```  
  
 CL 命令如下所示：  
  
```  
CL /Ob2 /Og MYAPP.C /link LIBC.LIB  
```  
  
 請注意有效地合併 命令列和的命令檔命令。  
  
## <a name="see-also"></a>請參閱  
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)