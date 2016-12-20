---
title: "強式名稱組件 (組件簽署) (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - ".NET Framework [C++], 組件簽署"
  - "組件 [C++]"
  - "組件 [C++], 簽署"
  - "連結器 [C++], 組件簽署"
  - "簽署組件"
  - "強式名稱組件 [C++]"
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 強式名稱組件 (組件簽署) (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題討論如何簽署組件 \(Assembly\)，通常指的是提供強式名稱給組件。  
  
## 備註  
 當使用 Visual C\+\+ 時，請使用連結器選項來簽署組件，以避免在組件簽署時發生與 CLR 屬性有關的問題：  
  
-   <xref:System.Reflection.AssemblyDelaySignAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyFileAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 之所以不使用屬性，是因為在組件中繼資料中看得到金鑰名稱，而如果檔案名稱含有機密資訊，就可能造成安全性的風險。  此外，如果您使用 CLR 屬性提供強式名稱給組件，然後在組件上執行類似 mt.exe 的事後處理工具，則 Visual C\+\+ 開發環境所使用的建置處理序將會使簽署組件的金鑰失效。  
  
 如果要在命令列上建置，請使用連結器選項簽署組件，然後執行事後處理工具 \(例如，mt.exe\)，您將會需要使用 sn.exe 重新簽署組件。  或者，您也可以建置並延遲簽署組件，並在執行事後處理工具之後，再完成簽署動作。  
  
 如果您在開發環境中建置時使用簽署屬性，您可以在建置後事件中明確呼叫 sn.exe \([Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)\)，以成功簽署組件。  如需詳細資訊，請參閱[指定建置事件](../ide/specifying-build-events.md)。  如果您使用屬性和建置後事件，則與使用連結器選項相較之下，可能會需要較少的建置時間。  
  
 下列連結器選項支援組件簽署：  
  
-   [\/DELAYSIGN \(部分簽署組件\)](../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYFILE \(指定金鑰或金鑰組以簽署組件\)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER \(指定金鑰容器以簽署組件\)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 如需強式組件的詳細資訊，請參閱[建立和使用強式名稱的組件](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)。  
  
## 請參閱  
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)