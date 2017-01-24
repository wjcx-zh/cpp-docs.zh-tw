---
title: "重新命名專案階層節點 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HierUtil7 範例 [Visual Studio SDK], 重新命名專案節點"
  - "專案節點, HierUtil7 範例中的重新命名"
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 重新命名專案階層節點 (C++)
您可以使用未受管理的 c \+ \+ 的 HierUtil7 專案架構，以重新命名專案資料夾的階層架構節點。  如需詳細資訊，請參閱 [HierUtil7 Sample](http://msdn.microsoft.com/zh-tw/29c15184-a70c-4813-86c2-fb1d47442d11)。  
  
## 展開階層架構節點  
  
#### 若要展開階層架構的節點，並重新命名資料夾  
  
1.  選取階層架構節點使用下列方法：  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode`是對應到該資料夾的階層架構容器和`EXPF_SelectItem`是從<xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS>列舉型別。  `GUID_MacroExplorer` Vsshell.idl 中定義為 GUID 常數，而且是範例`rguidPersistenceSlot`的函式簽名碼內`ExtExpand`，已定義在 Hu\_node.h 中。  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     您可以找到 Hu\_node.h 檔案在資料夾中，\< 安裝根 \> \\Program Files\\VSIP 8.0\\EnvSDK\\common\\hierutil7：  
  
2.  藉由張貼重新命名\] 命令，重新命名資料夾<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell`is a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> pointer: `<IVsUIShell>``srpVsUIShell`.  `guiVSStd97`是唯一的識別項的命令群組命令`cmdidRename`所屬 Vsshlids.h 所述。  
  
## 請參閱  
 [建立專案類型](../Topic/Creating%20Project%20Types.md)   
 [VSSDK 範例](../misc/vssdk-samples.md)