---
title: "如何：取消登錄 VSPackage | Microsoft Docs"
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
  - "範例應用程式 [Visual Studio SDK], 解除安裝"
  - "安裝程式, VSPackage"
ms.assetid: b51522f0-c033-4d93-b928-2171a953032b
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# 如何：取消登錄 VSPackage
根據預設，當您建置 VSPackage 時，會將其登錄到實驗登錄區。 在您完成實驗之後，實驗登錄區可能會充滿您不想要保留的 VSPackage。  
  
 若要刪除實驗登錄區中登錄的所有封裝，只要搭配使用 CreateExpInstance 工具和 \/Reset 選項重設登錄區即可。 如需詳細資訊，請參閱[實驗執行個體](../Topic/The%20Experimental%20Instance.md)。  
  
## 取消登錄個別 VSPackage  
  
#### 取消登錄 Unmanaged VSPackage  
  
1.  依序按一下 \[開始\] 和 \[執行\]，然後輸入 `regsvr32 /u`*pathToVSPackage.dll*，再按一下 \[確定\]。  
  
 由於 Unmanaged VSPackage 包含自我登錄程式碼，因此您可以使用 regsvr32 公用程式加以登錄和取消登錄。  
  
#### 取消登錄 Managed VSPackage  
  
1.  依序按一下 \[開始\] 和 \[執行\]，然後輸入 *Visual Studio SDK 安裝路徑*`\EnvSDK\tools\bin\x86\regpkg /unregister`*pathToVSPackage.dll*，再按一下 \[確定\]。  
  
 RegPkg 工具會讀取可內嵌於 Managed VSPackage 中的登錄屬性。**\/unregister** 參數會指示 RegPkg 以移除登錄中的資訊。  
  
## 請參閱  
 [Visual Studio Integration Samples](http://msdn.microsoft.com/zh-tw/b5dbf078-3af2-4fed-a1ea-171e4ee73a43)