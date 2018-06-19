---
title: -防護 （啟用防護檢查） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d05dd4f9d213c3d2729459486a9d0cfdbd79110
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375252"
---
# <a name="guard-enable-guard-checks"></a>/GUARD (啟用防護檢查)
指定在可執行映像中進行控制流程防護檢查的支援。  
  
## <a name="syntax"></a>語法  
  
```  
/GUARD:{CF|NO}  
```  
  
## <a name="remarks"></a>備註  
 當指定 /GUARD:CF 時，連結器會修改 .dll 或 .exe 的標頭，以表示控制流程防護 (CFG) 執行階段檢查的支援。 連結器也會將所需的控制項流程目標位址資料加入標頭。 根據預設，會停用 /GUARD:CF。 可以使用 /GUARD:NO 將其明確停用。 若要有效，/guard: cf 也需要[/DYNAMICBASE （使用位址空間配置隨機載入）](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)連結器選項，預設為開啟。  
  
 藉由編譯原始程式碼時[/guard: cf](../../build/reference/guard-enable-control-flow-guard.md)選項，編譯器分析控制流程藉由檢查所有可能目標位址的間接呼叫。 編譯器會插入程式碼，在執行階段確認間接呼叫指令的目標位址位於已知目標位址的清單中。 支援 CFG 的作業系統會停止無法通過 CFG 執行階段檢查的程式。 這使得攻擊者更難使用資料損毀變更呼叫目標來執行惡意程式碼。  
  
 必須同時對編譯器和連結器指定 /GUARD:CF 選項，以建立已啟用 CFG 的可執行檔映像。 已編譯，但未使用 /GUARD:CF 連結的程式碼會產生執行階段檢查的成本，但是不會啟用 CFG 保護。 若要指定 /guard: cf 選項時`cl`可編譯及連結在一個步驟中，編譯器的命令會將連結器旗標。 當**控制流程防護**Visual Studio 中設定屬性，/guard: cf 選項傳遞給編譯器和連結器。 當有分開編譯目的檔或程式庫時，必須在明確指定選項`link`命令。  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項  
  
1.  開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**，**連結器**，**命令列**。  
  
3.  在**其他選項**，輸入`/GUARD:CF`。  
  
## <a name="see-also"></a>另請參閱  
 [/guard （啟用控制流程防護）](../../build/reference/guard-enable-control-flow-guard.md)   
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)