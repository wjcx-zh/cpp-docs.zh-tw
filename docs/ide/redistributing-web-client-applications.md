---
title: 轉散發 Web 用戶端應用程式
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
ms.openlocfilehash: 37ff666493ada7dada19f5731e6581603d3cb57e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512409"
---
# <a name="redistributing-web-client-applications"></a>轉散發 Web 用戶端應用程式

如果您的應用程式使用實作 WebBrowser 控制項 (例如 `CHtmlView` 或 `CHtmlEditView`) 的 MFC 類別，則目標電腦上必須至少安裝 Microsoft Internet Explorer 4.0 或更新版本。

安裝最新版的 Internet Explorer 也可確保目標電腦有最新的通用控制項檔案。 如需詳細資訊，請參閱[安裝和部署 Internet Explorer 11](/internet-explorer/ie11-deploy-guide/install-and-deploy-ie11)。

## <a name="see-also"></a>請參閱

[部署傳統型應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)