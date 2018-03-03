---
title: "專案和方案檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.files.projectandsolution
dev_langs:
- C++
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 03797d266dc0f3104d6153b9d946d06ac963fafc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-and-solution-files"></a>專案和方案檔
當您在 Visual Studio 中建立專案時，會建立下列檔案。 它們可用來管理方案中的專案檔案。  
  
|Filename|目錄位置|方案總管位置|描述|  
|--------------|------------------------|--------------------------------|-----------------|  
|*Solname*.sln|*專案名稱*|不會顯示在方案總管中|*方案*檔案。 它會將專案的所有項目或多個專案組織成一個方案。|  
|*Projname*.suo|*專案名稱*|不會顯示在方案總管中|*方案選項*檔案。 它會儲存您的方案自訂，如此每當您在方案中開啟專案或檔案時，它會呈現您所要的外觀和行為。|  
|*Projname*.vcxproj|*專案名稱*|不會顯示在方案總管中|*專案*檔案。 它會儲存每個專案的特定資訊。 (在舊版中，這個檔案名為*Projname*.vcproj 或*Projname*.dsp。)如需 Visual c + + 專案檔的範例，請參閱[專案檔](../ide/project-files.md)。|  
|*Projname*.vcxitems|*專案名稱*|不會顯示在方案總管中|*共用的項目專案*檔案。 不會建置此專案。  相反地，專案可以參考另一個 c + + 專案，且其檔案會變成參考的專案建置程序的一部分。 這可以用來與跨平台 c + + 專案共用通用程式碼。|
|*Projname*.sdf|*專案名稱*|不會顯示在方案總管中|*瀏覽資料庫*檔案。 它支援瀏覽和導覽功能，例如**移至定義**，**尋找所有參考**，和**類別檢視**。 會藉由剖析標頭檔來產生它。|  
|*專案名稱。*vcxproj.filters|*專案名稱*|不會顯示在方案總管中|*篩選*檔案。 它指定要在方案的哪個位置加入檔案。 比方說，.h 檔案放**標頭檔**節點。|  
|*專案名稱。*.vcxproj.user|*專案名稱*|不會顯示在方案總管中|*移轉使用者*檔案。 從 Visual Studio 2008 移轉專案之後，此檔案包含任何 .vsprops 檔案轉換的資訊。|  
|*Projname*.idl|*專案名稱*|原始程式檔|(特定專案) 包含控制項類型程式庫的介面描述語言 (IDL) 原始程式碼。 Visual C++ 會使用這個檔案來產生類型程式庫。 產生的程式庫會向其他自動化用戶端公開控制項的介面。 如需詳細資訊，請參閱[介面定義 (IDL) 檔](http://msdn.microsoft.com/library/windows/desktop/aa378712)Windows SDK 中。|  
|Readme.txt|*專案名稱*|專案|*讀我檔案*檔案。 它是由應用程式精靈所產生，並說明專案中的檔案。|  
  
## <a name="see-also"></a>請參閱  
 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)