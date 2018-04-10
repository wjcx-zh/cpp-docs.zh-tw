---
title: -ALLOWISOLATION （資訊清單查閱） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0ca939021a6fc530b11c6ec66fc74cc012da1c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (資訊清單查閱)
指定資訊清單查閱的行為。  
  
## <a name="syntax"></a>語法  
  
```  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>備註  
 **/ALLOWISOLATION:NO**指出 Dll 會載入，因為如果有任何資訊清單，使連結器設定`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`選擇性標頭中的位元`DllCharacteristics`欄位。  
  
 **/ALLOWISOLATION**導致作業系統查閱和載入資訊清單。  
  
 **/ALLOWISOLATION**是預設值。  
  
 可執行檔停用隔離時，Windows 載入器並不會嘗試尋找新建立的處理序應用程式資訊清單。 新的處理序不會預設啟用內容，即使可執行檔或放置在相同的目錄名稱的可執行檔內部資訊清單*可執行檔名稱***.exe.manifest**。  
  
 如需詳細資訊，請參閱[資訊清單檔案參考](http://msdn.microsoft.com/library/aa375632)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**資訊清單檔案**屬性頁。  
  
5.  修改**允許隔離**屬性。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)