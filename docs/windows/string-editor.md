---
title: 字串編輯器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string.F1
dev_langs:
- C++
helpviewer_keywords:
- String editor
- string tables
- string tables, String editor
- string editing
- string editing, string tables
- resource editors, String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23211293313135cb0341ac234014ae3c144b7fec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891372"
---
# <a name="string-editor"></a>字串編輯器
字串資料表是一種 Windows 資源，包含了識別碼、值與應用程式所有字串標題的清單。 例如，狀態列提示位於字串資料表中。  
  
 在開發應用程式時，您可能會有多個字串資料表，每種語言或條件各使用一個。 但可執行的模組只會有一個字串資料表。 若您將資料表置於不同的 DLL 中，則執行中的應用程式可以參考多個字串資料表。  
  
 字串資料表讓您很容易就能將應用程式當地語系化成不同的語言。 若所有字串都位於同一個字串資料表，您只需翻凙字串 (及其他資源)，就能當地語系化應用程式，無須變更原始程式碼。 這種方式相較於手動尋找及取代原始程式檔中的各種字串更為理想。  
  
 您可以使用字串編輯器：  
  
-   [搜尋一或多個字串](../windows/finding-a-string.md)。  
  
-   快速 [插入新項目](../windows/adding-or-deleting-a-string.md) 到字串資料表中。  
  
-   [在資源檔案之間移動字串](../windows/moving-a-string-from-one-resource-file-to-another.md)  
  
-   [使用就地編輯的識別碼、值與標題屬性](../windows/changing-the-properties-of-a-string.md) ，並立即檢視變更。  
  
-   [變更多個字串的標題屬性](../windows/changing-the-caption-property-of-multiple-strings.md)  
  
-   [為字串加入格式或特殊字元](../windows/adding-formatting-or-special-characters-to-a-string.md)  
  
    > [!NOTE]
    >  Windows 不允許建立空的字串資料表。 若建立的字串資料表中不含任何項目，將會在您儲存資源檔案時自動予以刪除。  
  
 如需將資源加入至 managed 專案 （其會以 common language runtime 為目標） 的資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱 [逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) 和 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [資源編輯器](../windows/resource-editors.md)   
 [字串](http://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)   
 [關於字串](http://msdn.microsoft.com/library/windows/desktop/ms647465.aspx)

