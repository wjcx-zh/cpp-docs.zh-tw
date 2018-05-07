---
title: 轉散發 Web 用戶端應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92bd843b24ee13b3d606ba8bb4f4f1cc265e8e5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="redistributing-web-client-applications"></a>轉散發 Web 用戶端應用程式
如果您的應用程式會使用實作 WebBrowser 控制項的 MFC 類別 (例如，`CHtmlView`或`CHtmlEditView`)，Microsoft Internet Explorer 4.0 或更新版本必須至少使用最低限度安裝在目標電腦上。  
  
 安裝最新版的 Internet Explorer 也可確保目標電腦有最新的通用控制項的檔案。  
  
 安裝最少的 Internet Explorer 元件的相關資訊會提供下列知識庫文件中：  
  
-   Q185375、 如何： 建立單一的 EXE 安裝的 Internet Explorer ([http://support.microsoft.com/support/kb/articles/q185/3/75.asp](http://support.microsoft.com/support/kb/articles/q185/3/75.asp))  
  
 您可以在 MSDN Library 中，或在找到知識庫文章[ http://support.microsoft.com ](http://support.microsoft.com)。  
  
## <a name="see-also"></a>另請參閱  
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)