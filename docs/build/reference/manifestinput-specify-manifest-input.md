---
title: "-MANIFESTINPUT （指定資訊清單輸入） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a32eb8c65e14684b818341121714ce0359f6521a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (指定資訊清單輸入)
指定要包含在內嵌於影像中的資訊清單中的資訊清單輸入的檔。  
  
## <a name="syntax"></a>語法  
  
```  
/MANIFESTINPUT:filename  
```  
  
#### <a name="parameters"></a>參數  
 `filename`  
 要內嵌資訊清單中包含的資訊清單檔案。  
  
## <a name="remarks"></a>備註  
 **/MANIFESTINPUT**選項會指定要用來建立可執行映像中的內嵌資訊清單輸入檔的路徑。 如果您有多個資訊清單輸入檔，請使用此參數多次，每個輸入檔案一次。 資訊清單輸入的檔會合併，以建立內嵌資訊清單。 此選項需要**/manifest： 內嵌**選項。  
  
 無法設定此選項，直接在[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]。 請改用**額外的資訊清單檔案**要指定其他要包含的資訊清單檔案的專案屬性。 如需詳細資訊，請參閱[輸入和輸出、 資訊清單工具、 組態屬性、\<專案名稱 > 屬性頁對話方塊](../../ide/input-and-output-manifest-tool.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)