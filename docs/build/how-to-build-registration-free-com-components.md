---
title: 如何： 建置免註冊 COM 元件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e54327344d61cc70e68b528c5f88f3d30f5d185a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-build-registration-free-com-components"></a>如何：建置免註冊的 COM 元件
免註冊 COM 元件是內建於 Dll 的資訊清單的 COM 元件。  
  
### <a name="to-build-manifests-into-com-components"></a>建置 COM 元件資訊清單  
  
1.  開啟專案屬性頁之 COM 元件。  
  
2.  展開**組態屬性** 節點，然後展開**資訊清單工具**節點。  
  
3.  選取**輸入和輸出**屬性頁上，並將其設定**內嵌資訊清單**屬性等於**是**。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
5.  建置方案。  
  
## <a name="see-also"></a>另請參閱  
 [隔離的應用程式](http://msdn.microsoft.com/library/aa375190)   
 [關於-並存組件](http://msdn.microsoft.com/library/ff951640)   
 [如何：建置隔離的應用程式以使用 COM 元件](../build/how-to-build-isolated-applications-to-consume-com-components.md)