---
title: "部署概念 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b3aaf970e51f867d36cae288e8d025730093937
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="deployment-concepts"></a>部署概念
本章節將討論部署 c + + 應用程式的主要考量。  
  
## <a name="windows-installer-deployment-in-c"></a>C + + 中的 Windows Installer 部署  
 Visual c + + 專案通常會使用傳統的 Windows Installer 安裝程式進行部署。 若要準備的 Windows Installer 部署，您封裝應用程式中的 setup.exe 檔案，並發佈該程式檔連同的安裝程式套件 (.msi)。 然後執行 setup.exe 來安裝應用程式的使用者。  
  
 將應用程式封裝將安裝專案加入至您的方案;建置時，它會建立安裝程式和安裝程式散發給使用者的套件檔案。 如需詳細資訊，請參閱[選擇部署方法](../ide/choosing-a-deployment-method.md)。  
  
## <a name="library-dependencies"></a>程式庫相依性  
 C/c + + 應用程式建置時使用的 Visual c + + 程式庫所提供的功能，將會依存於這些程式庫，在執行階段存在。 為了讓應用程式執行，它必須連結，靜態或動態至必要的 Visual c + + 程式庫。 如果應用程式動態連結至 Visual c + + 程式庫，然後執行該程式庫時必須存在，載入它。 相反地，如果應用程式以靜態方式連結到 Visual c + + 程式庫，就不需要使用者的電腦上必須有對應的 Dll。 靜態連結中，不過，有部分負面的影響，例如增加應用程式檔案的大小和進行維護可能更困難。 如需詳細資訊，請參閱[使用 Dll 的優點](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls)。  
  
## <a name="packaging-and-redistributing"></a>封裝和轉散發  
 Visual c + + 程式庫會封裝為 Dll，並由 Visual Studio 開發人員的電腦上安裝所有必要的程式庫的 C/c + + 應用程式。 不過，在部署您的應用程式到您的使用者，不可行，在大部分情況下，要求他們來安裝 Visual Studio，才能執行您的應用程式。 請務必要能夠轉散佈剛才的部分 Visual c + + 所需的應用程式正確執行。  
  
 如需有關封裝和轉散發的詳細資訊，請參閱下列主題：  
  
-   [判斷要轉散發哪些 Dll](../ide/determining-which-dlls-to-redistribute.md)。  
  
-   [選擇部署方法](../ide/choosing-a-deployment-method.md)。  
  
 部署範例及有關疑難排解的建議，請參閱：  
  
-   [部署範例](../ide/deployment-examples.md)。  
  
-   [疑難排解 C/c + + 隔離應用程式和-並存組件](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)。  
  
## <a name="see-also"></a>另請參閱  
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [了解 Visual c + + 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)   
 [Windows Installer 部署](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)