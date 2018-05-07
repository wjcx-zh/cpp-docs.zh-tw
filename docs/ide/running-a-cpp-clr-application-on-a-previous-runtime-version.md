---
title: 在舊版的執行階段版本上執行的 c + + clr 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [C++], runtime version specified
- versions [C++]
- app.config files, runtime version specified
- compatibility [C++], runtime version specified
- backward compatibility [C++], runtime version specified
- application deployment [C++], runtime version specified
- common language runtime [C++], version specified
- deploying applications [C++], runtime version specified
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8e76930eb9191d27085d92a9d3a678812715fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>在舊版執行階段版本上執行 C++ /clr 應用程式
除非另行指定，c + +.NET Framework 應用程式已內建在 common language runtime (CLR) 版本，編譯器用來建置應用程式上執行。 不過，很可能針對一個版本提供必要的功能的任何其他版本上執行的執行階段所建置的.exe 應用程式。  
  
 若要完成這項作業，提供 包含執行階段版本資訊中的 app.config 檔案`supportedRuntime`標記。  
  
 在執行階段，app.config 檔案必須有表單的名稱*filename.ext*.config，其中*filename.ext*是啟動應用程式，可執行檔的名稱，而且必須使用相同的目錄中可執行檔。 例如，如果您的應用程式為 TestApp.exe，app.config 檔案會命名為 TestApp.exe.config。  
  
 如果您指定一個以上的執行階段版本，而且有多個已安裝執行階段版本的電腦上執行的應用程式，應用程式會使用組態檔中指定，且已安裝的第一個版本。  
  
 如需詳細資訊，請參閱[How to： 設定.NET Framework 版本為目標的應用程式](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)。  
  
 版本 1.0 或 1.1 版的 CLR，由 Visual c + + 所建置的應用程式上執行編譯器必須編譯使用[/clr:initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="see-also"></a>另請參閱  
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)