---
title: "了解 C/C++ 程式的資訊清單產生過程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資訊清單 [C++]"
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 了解 C/C++ 程式的資訊清單產生過程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[資訊清單](http://msdn.microsoft.com/library/aa375365)是 XML 文件，它可以是外部 XML 檔案，或是內嵌在應用程式或組件 \(Assembly\) 中的資源。  [隔離應用程式](http://msdn.microsoft.com/library/aa375190)的資訊清單檔是用來管理共用之並存組件的名稱和版本 \(應用程式應該要在執行階段繫結至這些組件\)。  [並存組件](_win32_side_by_side_assemblies)的資訊清單會指定組件對於名稱、版本、資源及其他組件的相依性。  
  
 有兩個方式可以建立隔離應用程式或並存組件的資訊清單。  首先，組件的作者可以遵循規則與命名需求，以手動方式建立資訊清單檔，  或者，如果程式僅相依於 CRT、MFC、ATL 或其他這類的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 組件，連結器即可自動產生資訊清單。  
  
 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫的標頭包含了組件資訊，而當程式庫加入到應用程式程式碼中時，連結器會使用這項組件資訊來組成最終二進位檔的資訊清單。  連結器不會將資訊清單檔內嵌到二進位檔內，而只會將此資訊清單產生為外部檔案。  將資訊清單當做外部檔案可能不適用於所有情況；  例如，建議私用組件最好要有內嵌的資訊清單。  在命令列組建中 \(例如使用 nmake 建置程式碼的組建\)，可以使用資訊清單工具來內嵌資訊清單；如需詳細資訊，請參閱[命令列的資訊清單產生過程](../build/manifest-generation-at-the-command-line.md)。  在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中建置時，可以在 \[**專案屬性**\] 對話方塊中設定資訊清單工具的屬性，以內嵌此資訊清單。如需詳細資訊，請參閱 [在 Visual Studio 中產生資訊清單](../build/manifest-generation-in-visual-studio.md)。  
  
## 請參閱  
 [隔離應用程式和並存組件的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [建置 C\/C\+\+ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)