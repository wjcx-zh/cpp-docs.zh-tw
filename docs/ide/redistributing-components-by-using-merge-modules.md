---
title: "使用合併模組轉散發元件 |Microsoft 文件"
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
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 093c732563844b14a3f99662150d4db9b2fac1fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-components-by-using-merge-modules"></a>使用合併模組來轉散發元件
Visual Studio 包含[合併模組](http://msdn.microsoft.com/library/aa367434)的授權與應用程式轉散發 Visual c + + 元件。 在 Windows Installer 安裝程式檔案中編譯合併模組時，會將特定 DLL 部署至具有特定平台的電腦。 在您的安裝程式檔中，指定應用程式必要條件的合併模組。 安裝 Visual Studio 時，合併模組會安裝在 \Program Files\Common Files\Merge 模組\\。 （只有非偵錯版本的 Visual c + + Dll 可能會轉散發。）連結的合併模組轉散發授權清單和詳細資訊，請參閱[轉散發 Visual c + + 檔案](../ide/redistributing-visual-cpp-files.md)。  
  
 若要啟用的可轉散發 Visual c + + Dll 安裝至 %SYSTEMROOT%\system32\ 資料夾，您可以使用合併模組。 （visual Studio 本身會使用這項技術）。不過，除非安裝的使用者具有系統管理員權限，否則安裝至此資料夾會失敗。  
  
 除非您不需要維護您的應用程式，而且未對於多個 DLL 版本具有相依性，否則建議您不要使用合併模組。 一個安裝程式中不可含有相同 DLL 的不同版本合併模組，而且合併模組會使得在應用程式之外獨立維護 DLL 變得困難。 相反地，我們建議您安裝 Visual c + + 可轉散發套件。  
  
## <a name="see-also"></a>請參閱  
 [轉散發 Visual C++ 檔案](../ide/redistributing-visual-cpp-files.md)