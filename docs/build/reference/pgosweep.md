---
title: "pgosweep |Microsoft 文件"
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
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 78ae6c36011e3c10359988cf2c501514d1bcf70a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pgosweep"></a>pgosweep
將所有設定檔資料執行中程式寫入.pgc 檔用於特性指引最佳化。  
  
## <a name="syntax"></a>語法  
  
```  
pgosweep [options] image pgcfile  
```  
  
#### <a name="parameters"></a>參數  
 `options`  
 選擇性參數，可以保留空白。 有效值`options`如下：  
  
-   **/?** 或**/help，**顯示說明訊息。  
  
-   **/noreset，**保留的執行階段資料結構中的計數。  
  
 `image`  
 使用編譯器選項 /ltcg: pginstrument 所建立的.exe 或.dll 檔案的完整路徑。  
  
 `pgcfile`  
 .Pgc 檔案，其中這個命令會寫出的資料計數。  
  
## <a name="remarks"></a>備註  
 此命令適用於使用 /ltcg: pginstrument 編譯器選項建置的程式。 它會中斷正在執行的程式，並將設定檔資料寫入至新的.pgc 檔案。 根據預設，命令會重設次數之後每一個寫入作業。 如果您指定**/noreset**選項時，命令將記錄的值，但不是會重設執行中的程式中。 此選項可讓您重複的資料如果您稍後擷取分析資料。  
  
 用於其他方面`pgosweep`是擷取應用程式僅供執行階段設定檔資訊。 例如，您可以執行`pgosweep`短時間內啟動應用程式，並捨棄該檔案之後。 這會移除與啟動成本相關聯的設定檔資料。 然後，您可以執行`pgosweep`再結束應用程式。 現在所收集的資料有只能從執行階段設定檔資訊。  
  
 .Pgc 檔案的名稱時 (`pgcfile`) 您可以使用標準格式，這是*appname ！ n*.pgc。 如果您使用此格式，編譯器會發現這項資料在 /ltcg: pgo 進行階段中。 如果您不使用標準格式，您必須使用[pgomgr](../../build/reference/pgomgr.md)合併的.pgc 檔案。  
  
## <a name="example"></a>範例  
  
```  
pgosweep myapp.exe myapp!1.pgc  
```  
  
 在此範例中，`pgosweep`寫入 myapp!1.pgc myapp.exe 的目前設定檔資訊。  
  
## <a name="see-also"></a>請參閱  
 [手動特性指引最佳化工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)