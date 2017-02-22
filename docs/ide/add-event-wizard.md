---
title: "加入事件精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.event.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "加入事件精靈 [C++]"
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 加入事件精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個精靈可將事件加入至 MFC ActiveX 控制項專案。  您可以指定自己的事件、自訂一般內建事件 \(Stock Event\) 或從內建事件清單選取。  
  
 **事件名稱**  
 設定 Automation 用戶端用來要求類別中事件的名稱。  輸入名稱或從清單中選取。  
  
 **事件類型**  
 指定要加入的事件類型。  只有從 \[事件名稱\] 清單中選取時才可以指定。  
  
|選項|描述|  
|--------|--------|  
|**內建**|指定將為這個類別實作的內建事件，例如按一下按鈕。  內建事件是在 MFC 程式庫中定義。|  
|**Custom**|指定您要自行提供事件實作 \(Implementation\)。|  
  
 **內部名稱**  
 設定傳送事件的成員 \(Member\) 函式名稱。  僅適用於自訂事件。  這個名稱根據 \[事件名稱\] 而定。  如果要提供與 \[事件名稱\] 不同的名稱，您可變更內部名稱。  
  
 **參數型別**  
 設定 \[參數名稱\] 的型別。  從清單中選取型別。  
  
 **參數名稱**  
 設定要透過事件傳遞的參數名稱。  在輸入名稱之後，您必須按一下 \[加入\] 以將它加入至參數清單。  
  
 按一下 \[加入\] 之後，參數名稱會出現在 \[**參數清單**\] 中。  
  
> [!NOTE]
>  如果您提供參數名稱，然後在按下 \[加入\] 之前按一下 \[完成\]，則參數不會加入至事件。  此時您必須尋找該方法，然後手動插入參數。 **參數清單**  
  
 **加入**  
 將您在 \[參數名稱\] 中指定的參數及其型別加入至 \[**參數清單**\]。  您必須按一下 \[加入\] 才能將參數加入清單。  
  
 **Remove**  
 將您在 \[**參數清單**\] 中選取的參數從清單中移除。  
  
 **參數清單**  
 顯示目前為方法加入的所有參數及其型別。  當您加入參數時，精靈會更新 \[**參數清單**\] 以顯示每個參數及其型別。  
  
## 請參閱  
 [加入事件](../ide/adding-an-event-visual-cpp.md)