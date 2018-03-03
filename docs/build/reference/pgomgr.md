---
title: "pgomgr |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8cbb9a4f8b92a1cd495e1312c1aa8a8f77cefcd3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pgomgr"></a>pgomgr
將分析資料從一個或多個.pgc 檔案加入至.pgd 檔。  
  
## <a name="syntax"></a>語法  
  
```  
pgomgr [options] pgcfiles pgdfile  
```  
  
#### <a name="parameters"></a>參數  
 `options`  
 Pgomgr 要可以指定下列選項：  
  
 **/help —**顯示可用 pgomgr 選項 (短，/？)。  
  
 **清除 / —**會使要清除所有的設定檔資訊的.pgd 檔。 您無法指定.pgc 檔**/清除**指定。  
  
 **/detail**-顯示詳細的統計資料，包括資料流程圖形涵蓋範圍資訊。  
  
 **摘要/**— 顯示每個函式的統計資料。  
  
 **唯一 /**-搭配使用時**/摘要**，原因裝飾函式名稱來顯示。  預設值，當 / 特點是未使用，為要顯示的未裝飾的函式名稱。  
  
 **/merge**[**:***n*]**—**會導致資料中要加入至.pgd 檔的.pgc 檔案。  選擇性參數，  *n* ，可讓您指定應該加入 hat 資料 *n* 時間。  比方說，如果案例通常執行 6 次，可以一次測試回合中執行並將它加入至.pgd 檔六次**pgomgr /merge:6**。  
  
 `pgcfiles`  
 一或多個.pgc 檔案您想要合併至.pgd 檔的設定檔資料。 您可以指定單一的.pgc 檔案或多個的.pgc 檔案。 如果您未指定任何.pgc 檔案，pgomgr 會將合併所有的.pgc 檔案的檔名是相同的.pgd 檔案。  
  
 `pgdfile`  
 .Pgd 檔案到您要合併的.pgc 檔案或檔案的資料。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  您只能從 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示字元啟動此工具。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。  
  
## <a name="example"></a>範例  
 在下列範例中，為.pgd 檔已清除的分析資料。  
  
```  
pgomgr /clear myapp.pgd  
```  
  
 在下列範例中，設定檔中的資料 myapp1.pgc 已加入至.pgd 檔 3 次。  
  
```  
pgomgr /merge:3 myapp1.pgc myapp.pgd  
```  
  
 在下列範例中，所有的 myapp #.pgc 檔案中的設定檔資料會加入至 myapp.pgd 檔案。  
  
```  
pgomgr -merge myapp1.pgd  
```  
  
## <a name="see-also"></a>請參閱  
 [手動特性指引最佳化工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)