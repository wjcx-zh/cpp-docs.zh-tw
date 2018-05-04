---
title: 建置 C/c + + 隔離應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69de94159ef792aedff35efe81e8bb663d571105
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="building-cc-isolated-applications"></a>建置 C/C++ 隔離應用程式
隔離的應用程式只依賴-並存組件，並繫結至其使用資訊清單的相依性。 不需要完全隔離，才能執行正確 Windows; 上的應用程式不過，由投資導致完全隔離的應用程式，如果您需要服務應用程式在未來可能節省時間。 讓您完全隔離的應用程式的優點的資訊，請參閱[隔離的應用程式](http://msdn.microsoft.com/library/aa375190)。  
  
 當您建置原生 C/c + + 應用程式使用 Visual c + + 時，根據預設 Visual Studio 專案系統會產生描述您的應用程式相依性，在 Visual c + + 程式庫上的資訊清單檔案。 如果這些相依性只應用程式具有，接著它會變成隔離的應用程式，因為它會重建與 Visual Studio。 如果您的應用程式使用其他程式庫，在執行階段，則您可能需要重建這些程式庫做為-並存組件中所述的步驟[建置 C/c + + 並存組件](../build/building-c-cpp-side-by-side-assemblies.md)。  
  
## <a name="see-also"></a>另請參閱  
 [隔離的應用程式和-並存組件的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [建置 C/C++ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)