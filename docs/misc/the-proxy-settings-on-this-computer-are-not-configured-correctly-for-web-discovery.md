---
title: "尚未正確設定這部電腦的 Proxy 設定以進行 Web 探索。 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_MUSTSPECIFYPROXYSERVER"
  - "vs.WebDiscoveryProxyHelp"
ms.assetid: aea2cc20-9180-47cb-b1ed-78fa5f8a407f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 尚未正確設定這部電腦的 Proxy 設定以進行 Web 探索。
如果您想要在防火牆後方的電腦上進行開發，但尚未明確地為 Internet Explorer 連線指定 Proxy 伺服器，\[加入 Web 參考\] 對話方塊中就會出現這個錯誤。 您必須明確指定 Proxy 伺服器在網路上的位址和連接埠，才能讓 \[加入 Web 參考\] 對話方塊中的網頁瀏覽器可以使用防火牆外部的服務。 .NET Framework 會忽略 Internet Explorer 連線的自動偵測 Proxy 選項。 您可能必須向網路系統管理員詢問這項 Proxy 資訊。  
  
 如需「防火牆和 Web Proxy 用戶端的自動探索」的詳細資訊，請參閱︰[http:\/\/www.microsoft.com\/technet\/prodtechnol\/isa\/2004\/plan\/automaticdiscovery.mspx](http://www.microsoft.com/technet/prodtechnol/isa/2004/plan/automaticdiscovery.mspx)  
  
### 為 Internet Explorer 指定 Proxy 伺服器  
  
1.  從 \[工具\] 功能表選擇 \[選項\]。  
  
2.  在 \[選項\] 對話方塊中，依序選擇 \[環境\] 和 \[網頁瀏覽器\]。  
  
3.  按一下 \[Internet Explorer 選項\]。  
  
4.  在 \[連線\] 索引標籤上，按一下 \[區域網路設定\]。  
  
5.  取消選取 \[自動偵測設定\]。  
  
6.  在 \[Proxy 伺服器\] 區域中，選取 \[在您的區域網路使用 Proxy 伺服器 \(這些設定將不會套用到撥號或 VPN 連線\)\]。  
  
7.  指定符合您網路的位址和連接埠號碼。  
  
8.  依序按一下 \[確定\] 和 \[確定\]，然後再按一下 \[確定\]。  
  
9. 從 \[檔案\] 功能表選擇 \[結束\]，然後重新開啟 Visual Studio。  
  
## 請參閱  
 [NIB：加入 Web 參考對話方塊](http://msdn.microsoft.com/zh-tw/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [NIB：如何：加入和移除 Web 參考](http://msdn.microsoft.com/zh-tw/a7ddaa5d-4672-405b-91b3-39de65d7e3a2)   
 [Programming the Web with XML Web Services](http://msdn.microsoft.com/zh-tw/2d651a26-73df-4b39-85fa-7913a7d6bee4)