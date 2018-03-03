---
title: "了解自訂建置步驟和建置事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9abb7ff0b9a39656999e7a53b476056f7a5b1558
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-custom-build-steps-and-build-events"></a>了解自訂建置步驟和建置事件
從在 Visual c + + 開發環境中，有三種基本方式，以自訂建置程序：  
  
 **自訂建置步驟**  
 自訂建置步驟是與專案相關聯的建置規則。 自訂建置步驟可以指定任何其他輸入或輸出檔案和要顯示的訊息執行命令列。 如需詳細資訊，請參閱[How to： 將自訂建置步驟加入至 MSBuild 專案](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)。  
  
 **自訂建置工具**  
 自訂建置工具是一個或多個檔案與相關聯的建置規則。 自訂建置步驟可以將輸入的檔傳遞至自訂建置工具，會導致一個或多個輸出檔案。 例如，MFC 應用程式中的說明檔是建置與自訂建置工具。 如需詳細資訊，請參閱[如何： 加入自訂建置工具 MSBuild 專案](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)和[指定自訂建置工具](../ide/specifying-custom-build-tools.md)。  
  
 **建置事件**  
 建置事件可讓您自訂在專案的組建。 有三個建置事件：*建置前*，*連結前*，和*建置後*。 建置事件可讓您指定要在建置流程中的特定時間發生的動作。 例如，您可以使用建置事件，若要註冊的檔案**regsvr32.exe**專案完成建置後。 如需詳細資訊，請參閱[指定建置事件](../ide/specifying-build-events.md)。  
  
 [疑難排解組建自訂](../ide/troubleshooting-build-customizations.md)可協助您確認您的自訂建置步驟，然後建置事件如預期般執行。  
  
 輸出格式的自訂建置步驟或建置事件，也可讓此工具的可用性。 如需詳細資訊，請參閱[格式化自訂建置步驟或建置事件的輸出](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md)。  
  
 建置事件和自訂建置步驟會依下列順序，以及其他建置步驟執行：  
  
1.  建置前事件  
  
2.  自訂建置工具的個別檔案  
  
3.  MIDL  
  
4.  資源編譯器  
  
5.  C/c + + 編譯器  
  
6.  連結前事件  
  
7.  連結器或管理員 （視情況）  
  
8.  資訊清單工具  
  
9. BSCMake  
  
10. 在專案上的自訂建置步驟  
  
11. 建置後事件  
  
 `custom build step on the project`和`post-build event`執行所有其他組建之後，依序處理完成。  
  
## <a name="see-also"></a>請參閱  
 [在 Visual Studio 中建置 c + + 專案](../ide/building-cpp-projects-in-visual-studio.md)   
 [建置命令和屬性的一般巨集](../ide/common-macros-for-build-commands-and-properties.md)   
 [工具建置順序 對話方塊](http://msdn.microsoft.com/en-us/6204c5b1-7ce9-4948-9ff6-0268642ee14c)