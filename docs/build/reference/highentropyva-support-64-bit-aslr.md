---
title: "-HIGHENTROPYVA (支援 64 位元 ASLR) |Microsoft 文件"
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
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 059f6169cafc48fc67587ae2f5827966269e6ac7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (支援 64 位元 ASLR)
指定可執行映像支援高熵 64 位元位址空間配置隨機載入 (ASLR)。  
  
## <a name="syntax"></a>語法  
  
```  
/HIGHENTROPYVA[:NO]  
```  
  
## <a name="remarks"></a>備註  
 根據預設，會針對 64 位元可執行映像開啟 /HIGHENTROPYVA。 它不適用於 32 位元可執行檔映像。 若要啟用此選項，也必須開啟 /DYNAMICBASE。  
  
 /HIGHENTROPYVA 修改 .dll 檔或 .exe 檔的標頭，以指示是否支援 64 位元位址的 ASLR。 在可執行檔和它所依據的所有模組上設定此選項時，支援 64 位元 ASLR 的作業系統可以使用 64 位元虛擬位址空間中的隨機位址，在載入時間為可執行檔映像的區段重定基底。 這個大型位址空間會使攻擊者較難猜到特定記憶體區域的位置。  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項  
  
1.  開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**命令列**屬性頁。  
  
5.  在**其他選項**，輸入`/HIGHENTROPYVA`或`/HIGHENTROPYVA:NO`。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)