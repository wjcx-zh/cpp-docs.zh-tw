---
title: "加入事件精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.event.overview
dev_langs: C++
helpviewer_keywords: Add Event Wizard [C++]
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 62ecbe7dece323ce5e99fbe32b3b936fe3661362
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="add-event-wizard"></a>加入事件精靈
此精靈會將事件加入至 MFC ActiveX 控制項專案。 您可以指定您自己的事件，您可以自訂的一般內建的事件，或您可以從內建事件的清單中選取。  
  
 **事件名稱**  
 設定由 Automation 用戶端用來向類別要求事件的名稱。 輸入名稱，或從清單中選取一個。  
  
 **事件類型**  
 表示要加入事件的類型。 只有當您選取從可用**事件名稱**清單。  
  
|選項|描述|  
|------------|-----------------|  
|**內建**|指定內建的事件，例如按一下按鈕，將會實作這個類別。 Microsoft Foundation Class (MFC) 程式庫中定義內建事件。|  
|**自訂**|指定您要提供您自己的實作的事件。|  
  
 **內部名稱**  
 設定傳送事件的成員函式的名稱。 僅適用於自訂的事件。 名稱根據**事件名稱**。 如果您想要提供不同的名稱，您可以變更的內部名稱**事件名稱**。  
  
 **參數型別**  
 設定類型**參數名稱**。 從清單中選取類型。  
  
 **參數名稱**  
 設定要透過您的事件傳遞的參數名稱。 輸入名稱之後, 您必須按一下**新增**，將它加入的參數清單。  
  
 一旦您按一下**新增**，參數名稱會出現在**參數清單**。  
  
> [!NOTE]
>  如果您提供參數名稱，然後按一下**完成**您按一下前**新增**，則參數不會加入至事件。 您必須尋找的方法，並手動插入參數。 **參數清單**  
  
 **[新增]**  
 將您在中指定的參數加入**參數名稱**，和其類型，以**參數清單**。 您必須按一下**新增**將參數新增至清單。  
  
 **移除**  
 移除在選取的參數**參數清單**從清單中。  
  
 **參數清單**  
 顯示所有參數及其目前已加入的方法的類型。 加入參數時，精靈會更新**參數清單**以顯示每個參數的型別。  
  
## <a name="see-also"></a>請參閱  
 [加入事件](../ide/adding-an-event-visual-cpp.md)