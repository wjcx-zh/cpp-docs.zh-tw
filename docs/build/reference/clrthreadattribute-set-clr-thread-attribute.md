---
title: "-CLRTHREADATTRIBUTE （設定 CLR 執行緒屬性） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
dev_langs:
- C++
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f1aae2dadc2fa7a8c9dc67780bb88b4da60d256e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (設定 CLR 執行緒屬性)
明確指定 CLR 程式進入點的 threading 屬性。  
  
## <a name="syntax"></a>語法  
  
```  
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}  
```  
  
#### <a name="parameters"></a>參數  
 MTA  
 套用 MTAThreadAttribute 屬性至程式的進入點。  
  
 無  
 與不指定 /CLRTHREADATTRIBUTE 相同。  可讓 Common Language Runtime (CLR) 設定預設的執行緒屬性。  
  
 STA  
 套用 STAThreadAttribute 屬性至程式的進入點。  
  
## <a name="remarks"></a>備註  
 設定執行緒屬性時才有效建置.exe，因為它影響到主執行緒的進入點。  
  
 如果您使用的預設進入點 （main 或 wmain，例如） 的執行緒模型使用指定 /CLRTHREADATTRIBUTE 或放入執行緒屬性 （STAThreadAttribute 或 MTAThreadAttribute） 上的預設項目函式。  
  
 如果您使用非預設進入點時，指定使用 /CLRTHREADATTRIBUTE 或放入執行緒在非預設項目函式中，屬性，然後指定非預設進入點使用的執行緒模型[/ENTRY](../../build/reference/entry-entry-point-symbol.md).  
  
 如果指定 /CLRTHREADATTRIBUTE 的執行緒模型不一致的原始程式碼中指定的執行緒模型，將會忽略 /CLRTHREADATTRIBUTE 連結器，並套用原始程式碼中指定的執行緒模型。  
  
 它可能需要您使用單一執行緒，例如，如果您的 CLR 程式裝載使用單一執行緒 COM 物件。  如果您的 CLR 程式使用多執行緒處理，它無法裝載使用單一執行緒 COM 物件。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**進階**屬性頁。  
  
5.  修改**CLR 執行緒屬性**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)