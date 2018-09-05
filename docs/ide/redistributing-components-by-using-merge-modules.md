---
title: 使用合併模組來轉散發元件 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d816d932ce518e006e5537075fe4ac7782362ad4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206980"
---
# <a name="redistributing-components-by-using-merge-modules"></a>使用合併模組來轉散發元件
Visual Studio 包含授權用於與應用程式轉散發的各個 Visual C++ 元件的[合併模組](/windows/desktop/Msi/about-merge-modules)。 在 Windows Installer 安裝程式檔案中編譯合併模組時，會將特定 DLL 部署至具有特定平台的電腦。 在您的安裝程式檔中，指定應用程式必要條件的合併模組。 安裝 Visual Studio 後，合併模組會安裝於 \Program Files\Common Files\Merge Modules\\。 (只可轉散發非偵錯版本的 Visual C++ DLL。)如需關於授權用於轉散發之合併模組清單的連結和詳細資訊，請參閱[轉散發 Visual C++ 檔案](../ide/redistributing-visual-cpp-files.md)。  
  
 您可以使用合併模組將可轉散發 Visual C++ DLL 安裝至 %SYSTEMROOT%\system32\ 資料夾。 (Visual Studio 本身即使用這項技術。)不過，除非安裝的使用者具有系統管理員權限，否則安裝至此資料夾會失敗。  
  
 除非您不需要維護您的應用程式，而且未對於多個 DLL 版本具有相依性，否則建議您不要使用合併模組。 一個安裝程式中不可含有相同 DLL 的不同版本合併模組，而且合併模組會使得在應用程式之外獨立維護 DLL 變得困難。 相反地，我們建議您安裝 Visual C++ 可轉散發套件。  
  
## <a name="see-also"></a>請參閱  
 [轉散發 Visual C++ 檔案](../ide/redistributing-visual-cpp-files.md)