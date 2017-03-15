---
title: "/GUARD (啟用防護檢查) | Microsoft Docs"
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
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# /GUARD (啟用防護檢查)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定在可執行檔映像中進行控制流程防護檢查的支援。  
  
## 語法  
  
```  
/GUARD:{CF|NO}  
```  
  
## 備註  
 當指定 \/GUARD:CF 時，連結器會修改 .dll 或 .exe 的標頭，以表示控制流程防護 \(CFG\) 執行階段檢查的支援。  連結器也會將所需的控制項流程目標位址資料加入標頭。  根據預設，會停用 \/GUARD:CF。  可以使用 \/GUARD:NO 將其明確停用。  若要變得有效，\/GUARD:CF 也需要 [\/DYNAMICBASE \(使用位址空間隨機載入\)](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) 連結器選項，其預設為開啟。  
  
 當使用 [\/guard:cf](../../build/reference/guard-enable-control-flow-guard.md) 選項編譯原始程式碼時，編譯器會藉由檢查所有可能目標位址的間接呼叫來分析控制流程。  編譯器會插入程式碼，在執行階段確認間接呼叫指令的目標位址位於已知目標位址的清單中。  支援 CFG 的作業系統會停止無法通過 CFG 執行階段檢查的程式。  這使得攻擊者更難使用資料損毀變更呼叫目標來執行惡意程式碼。  
  
 必須同時對編譯器和連結器指定 \/GUARD:CF 選項，以建立已啟用 CFG 的可執行檔映像。  已編譯，但未使用 \/GUARD:CF 連結的程式碼會產生執行階段檢查的成本，但是不會啟用 CFG 保護。  對 `cl` 命令指定 \/GUARD:CF 選項，以在一個步驟中編譯及連結時，編譯器會將此旗標傳遞給連結器。  在 Visual Studio 中設定 \[控制流程防護\] 屬性時，\/GUARD:CF 選項會同時傳遞至編譯器和連結器。  分開編譯物件檔案或程式庫時，必須在 `link` 命令明確指定選項。  
  
### 在 Visual Studio 中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  依序展開 \[組態屬性\]、\[連結器\]、\[命令列\]。  
  
3.  在 \[其他選項\] 中，輸入 `/GUARD:CF`。  
  
## 請參閱  
 [\/guard \(啟用控制流程防護\)](../../build/reference/guard-enable-control-flow-guard.md)   
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)