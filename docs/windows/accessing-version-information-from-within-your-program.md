---
title: "存取您的程式內的版本資訊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.version
dev_langs: C++
helpviewer_keywords:
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 56fde0710f8156474922afb557b799d9d4c0ad8e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="accessing-version-information-from-within-your-program"></a>從您的程式內存取版本資訊
### <a name="to-access-version-information-from-within-your-program"></a>存取程式內的版本資訊  
  
1.  如果您想要存取程式內的版本資訊，請使用 [GetFileVersionInfo](http://msdn.microsoft.com/library/windows/desktop/ms647003.aspx) 函式和 [VerQueryValue](http://msdn.microsoft.com/library/windows/desktop/ms647464.aspx) 函式。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](https://msdn.microsoft.com/library/f45fce5x.aspx)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](https://msdn.microsoft.com/library/xbx3z216.aspx)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](https://msdn.microsoft.com/library/h6270d0z.aspx)。  
  
 **Requirements**  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [版本資訊編輯器](../windows/version-information-editor.md)   
 [版本資訊 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)

