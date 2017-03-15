---
title: "/MANIFESTINPUT (指定資訊清單輸入) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# /MANIFESTINPUT (指定資訊清單輸入)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定資訊清單輸入檔案，以包含在影像內嵌的資訊清單中。  
  
## 語法  
  
```c#  
/MANIFESTINPUT:filename  
```  
  
#### 參數  
 `filename`  
 要加入內嵌資訊清單內嵌清單檔案。  
  
## 備註  
 **\/MANIFESTINPUT** 選項指定輸入檔的路徑，用來建立可執行檔映像的內嵌資訊清單。  如果您有多個資訊清單輸入檔案，請多次使用參數 \(為每個輸入檔案各使用一次\)。  資訊清單輸入檔案會合併以建立內嵌資訊清單。  這個選項必需配合 **\/MANIFEST:EMBED** 選項。  
  
 這個選項無法直接在 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 中設定。  相反地，請改用專案的 \[**其他資訊清單檔**\] 屬性指定要包含的其他資訊清單檔。  如需詳細資訊，請參閱[輸入和輸出、資訊清單工具、組態屬性、\<Projectname\> 屬性頁對話方塊](../../ide/input-and-output-manifest-tool.md)。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)