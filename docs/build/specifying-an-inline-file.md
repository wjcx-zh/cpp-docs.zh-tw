---
title: 指定內嵌檔 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ef2183390b2aca2fb54e1468bd59e697374a355a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-an-inline-file"></a>指定內嵌檔
指定兩個角括弧 (<<) 命令中其中*filename*出現。 角括號不可為巨集展開。  
  
## <a name="syntax"></a>語法  
  
```  
<<[filename]  
```  
  
## <a name="remarks"></a>備註  
 執行命令時，會取代角括號*filename*，如果指定，或將 NMAKE 產生的唯一名稱。 如果指定， *filename*必須遵循不含空格或定位鍵的角括號。允許的路徑。 需要或假設沒有副檔名。 如果*filename*指定的檔案建立在目前或指定的目錄，覆寫任何現有的檔案名稱; 否則它會建立在 TMP 目錄中 (或目前的目錄中，如果 TMP 環境變數未定義）。 如果使用上一個*filename*是重複使用，NMAKE 會取代先前的檔案。  
  
## <a name="see-also"></a>請參閱  
 [Makefile 中的內嵌檔](../build/inline-files-in-a-makefile.md)