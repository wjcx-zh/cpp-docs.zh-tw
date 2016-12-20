---
title: "疑難排解例外狀況：System.InvalidOperationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidOperationException 類別"
ms.assetid: db3400e5-62d7-4d65-897d-387e7edcb7cf
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.InvalidOperationException
呼叫物件的方法時，若物件的狀態無法支援方法呼叫，會擲回 <xref:System.InvalidOperationException?displayProperty=fullName>。 方法嘗試從非主執行緒或 UI 執行緒的執行緒操作 UI 時，也會擲回例外狀況。  
  
> [!IMPORTANT]
>  因為 可能在各種不同的情況下擲回 <xref:System.InvalidOperationException>，所以請務必閱讀並了解例外狀況助理中所顯示的 <xref:System.Exception.Message%2A>。  
  
##  <a name="BKMK_In_this_article"></a> 本文內容  
 [在非 UI 執行緒上執行以更新 UI 的方法](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
 [變更其逐一查看的集合之 foreach (Visual Basic 中的 For Each) 區塊中的陳述式](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
 [將 Null 轉換成 T 的 Nullable&lt;T&gt;](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
 [在空集合上呼叫的 System.Linq.Enumerable 方法](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
 [相關文章](#BKMK_Related_articles)  
  
 本文中的程式碼範例，示範一些會在您的應用程式中發生的常見 <xref:System.InvalidOperationException> 例外狀況。處理問題的方式需視特定情況而定。如果對應用程式功能而言是嚴重錯誤的例外狀況，您可能要使用 [try … catch](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md) \(Visual Basic 中的 [Try .. Catch](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)\) 建構函式來擷取例外狀況，並清除應用程式的狀態，再結束應用程式。但可以預測並避免其他 <xref:System.InvalidOperationException>。修改過的方法範例會示範一些此類技術。  
  
##  <a name="BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI"></a> 在非 UI 執行緒上執行以更新 UI 的方法  
 [從非 UI 執行緒更新 UI 造成 InvalidOperationException](#BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread)  **&#124;**  [避免非 UI 執行緒上的 InvalidOperationExceptions](#BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads)  
  
 大部分 .NET GUI \(圖形化使用者介面\) 應用程式架構，例如 Windows Form 和 Windows Presentation Foundation \(WPF\)，可讓您只從建立及管理 UI 的執行緒 \(**主要**或 **UI** 執行緒\) 存取 GUI 物件。 嘗試從非 UI 執行緒存取 UI 元素時，會擲回 <xref:System.InvalidOperationException>。  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_a_UI_update_from_a_non_UI_thread"></a> 從非 UI 執行緒更新 UI 造成 InvalidOperationException  
  
> [!NOTE]
>  下列範例使用[Task\-based Asynchronous Pattern \(TAP\)](../Topic/Task-based%20Asynchronous%20Pattern%20\(TAP\).md)來建立非 UI 執行緒。 不過，這些範例也與所有 .NET [Asynchronous Programming Patterns](../Topic/Asynchronous%20Programming%20Patterns.md)相關。  
  
 在這些範例中，`ThreadsExampleBtn_Click` 事件處理常式會呼叫 `DoSomeWork` 方法兩次。 第一次呼叫的方法 \(`DoSomeWork(20);` 會同步執行並成功。 但第二次呼叫 \(`Task.Run( () => { DoSomeWork(1000);});`\) 是在應用程式之[執行緒集區](http://msdn.microsoft.com/en-us/library/system.threading.threadpool.aspx)的執行緒上執行。 由於這個呼叫會嘗試從非 UI 執行緒更新 UI，所以此陳述式擲回 <xref:System.InvalidOperationException>。  
  
 **WPF 和市集應用程式**  
  
> [!NOTE]
>  在手機的市集應用程式中，會擲回 <xref:System.Exception>，而不是更特定的 <xref:System.InvalidOperationException>。  
  
 **例外狀況訊息：**  
  
|||  
|-|-|  
|WPF 應用程式|其他資訊: 呼叫執行緒無法存取此物件，因為此物件屬於另一個執行緒。|  
|市集應用程式|其他資訊: 應用程式所呼叫了整理給不同執行緒的介面。 \(但 HRESULT: 0x8001010E \(RPC\_E\_WRONG\_THREAD\) 除外\)|  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, RoutedEventArgs e) { TextBox1.Text = String.Empty; TextBox1.Text = "Simulating work on UI thread.\n"; DoSomeWork(20); TextBox1.Text += "Simulating work on non-UI thread.\n"; await Task.Run(() => DoSomeWork(1000)); TextBox1.Text += "ThreadsExampleBtn_Click completes. "; } private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); TextBox1.Text += msg; }  
```  
  
 **Windows Forms 應用程式**  
  
 **例外狀況訊息：**  
  
-   其他資訊: 跨執行緒作業無效: 存取控制項 'TextBox1' 時所使用的執行緒與建立控制項的執行緒不同。  
  
```c#  
private async void ThreadsExampleBtn_Click(object sender, EventArgs e) { TextBox1.Text = String.Empty; var tbLinesList = new List<string>() {"Simulating work on UI thread."}; TextBox1.Lines = tbLinesList.ToArray(); DoSomeWork(20, tbLinesList); tbLinesList.Add("Simulating work on non-UI thread."); TextBox1.Lines = tbLinesList.ToArray(); await Task.Run(() => DoSomeWork(1000, tbLinesList)); tbLinesList.Add("ThreadsExampleBtn_Click completes."); TextBox1.Lines = tbLinesList.ToArray(); } private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { }; { // spin }; // report completion var msg = String.Format("Some work completed in {0} ms on UI thread. \n", msOfWork); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); }  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文內容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [在非 UI 執行緒上執行以更新 UI 的方法](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_on_non_UI_threads"></a> 避免非 UI 執行緒上的 InvalidOperationExceptions  
 Windows UI 架構實作了*「發送器」*\(dispatcher\) 模式，其中包含檢查是否正在 UI 執行緒上執行對 UI 元素成員呼叫的方法，以及在 UI 執行緒上排定呼叫的其他方法。  
  
 **WPF 應用程式**  
  
 在 WPF 應用程式中，使用其中一個 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> 方法來執行 UI 執行緒上的委派。 如果有必要，請使用 <xref:System.Windows.Threading.Dispatcher.CheckAccess%2A?displayProperty=fullName> 方法，以判斷某個方法是否執行於非 UI 執行緒上。  
  
```c#  
private void DoSomeWork(int msOfWork) { var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.CheckAccess()) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); Action act = ()=> {TextBox1.Text += msg;}; TextBox1.Dispatcher.Invoke(act); } }  
  
```  
  
 **Windows Forms 應用程式**  
  
 在 Windows Form 應用程式中，使用 <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> 方法來執行更新 UI 執行緒的委派。 如果有必要，請使用 <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> 屬性，以判斷某個方法是否執行於非 UI 執行緒上。  
  
```c#  
private void DoSomeWork(int msOfWork, List<string> tbLinesList) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.InvokeRequired) { msg = String.Format(msgFormat, msOfWork, "non-"); tbLinesList.Add(msg); Action act = () => TextBox1.Lines = tbLinesList.ToArray(); TextBox1.Invoke( act ); } else { msg = String.Format(msgFormat, msOfWork, String.Empty); tbLinesList.Add(msg); TextBox1.Lines = tbLinesList.ToArray(); } }  
```  
  
 **市集應用程式**  
  
 在市集應用程式中，使用 <xref:Windows.UI.Core.CoreDispatcher.RunAsync%2A?displayProperty=fullName> 方法來執行更新 UI 執行緒的委派。 如果有必要，請使用 <xref:Windows.UI.Core.CoreDispatcher.HasThreadAccess%2A> 屬性，以判斷某個方法是否執行於非 UI 執行緒上。  
  
```c#  
private void DoSomeWork(int msOfWork) { // simulate work var endTime = DateTime.Now.AddMilliseconds(msOfWork); while (DateTime.Now < endTime) { // spin }; // report completion var msgFormat = "Some work completed in {0} ms on {1}UI thread.\n"; var msg = String.Empty; if (TextBox1.Dispatcher.HasThreadAccess) { msg = String.Format(msgFormat, msOfWork, String.Empty); TextBox1.Text += msg; } else { msg = String.Format(msgFormat, msOfWork, "non-"); TextBox1.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,()=> {TextBox1.Text += msg;}); } }  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文內容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [在非 UI 執行緒上執行以更新 UI 的方法](#BKMK_A_method_running_on_a_non_UI_thread_updates_the_UI)  
  
##  <a name="BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating"></a> 變更其逐一查看的集合之 foreach \(Visual Basic 中的 For Each\) 區塊中的陳述式  
 [使用 foreach 造成 InvalidOperationException](#BKMK_Causing_an_InvalidOperationException_with_foreach)  **&#124;**  [避免迴圈中的 InvalidOperationExceptions](#BKMK_Avoiding_InvalidOperationExceptions_in_loops)  
  
 [Foreach](../Topic/foreach,%20in%20\(C%23%20Reference\).md) 陳述式 \(Visual Basic 中的 [For Each](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md)\)，會為陣列或集合中實作 <xref:System.Collections.IEnumerable?displayProperty=fullName> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 介面的每個元素，重複內嵌的陳述式群組。`foreach` 陳述式可用來逐一查看集合，以讀取和修改元素，但它不能用來新增或移除集合中的元素。 如果您在 foreach 陳述式中，新增或移除來源集合的元素，會擲回 <xref:System.InvalidOperationException>。  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_foreach"></a> 使用 foreach 造成 InvalidOperationException  
 在這個範例中，<xref:System.InvalidOperationException> 陳述式嘗試修改 foreach 區塊中的清單時，就會擲回 `numList.Add(5);`。  
  
 **例外狀況訊息：**  
  
-   其他資訊: 集合已修改; 列舉操作可能無法執行。  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文內容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [變更其逐一查看的集合之 foreach (Visual Basic 中的 For Each) 區塊中的陳述式](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
###  <a name="BKMK_Avoiding_InvalidOperationExceptions_in_loops"></a> 避免迴圈中的 InvalidOperationExceptions  
  
> [!IMPORTANT]
>  逐一查看集合時，如果對清單新增或移除元素，可能會有非預期且很難預測的副作用。 如果可能的話，您應該移動反覆運算之外的作業。  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 如果您的情況需要在逐一查看集合時，對清單新增或移除元素，請使用 [for](../Topic/for%20\(C%23%20Reference\).md) \(Visual Basic 中的 [For](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)\) 迴圈：  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文內容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [變更其逐一查看的集合之 foreach (Visual Basic 中的 For Each) 區塊中的陳述式](#BKMK_A_statement_in_a_foreach_For_Each_in_Visual_Basic_block_changes_the_collection_it_is_iterating)  
  
##  <a name="BKMK_A_Nullable_T_that_is_null_is_cast_to_T"></a> 將 Null 轉換成 T 的 Nullable\<T\>  
 [無效的轉換造成 InvalidOperationException](#BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast)  **&#124;**  [從錯誤的轉換避免 InvalidOperationException](#BKMK_Avoiding_InvalidOperationException_from_a_bad_cast)  
  
 如果您轉換的 <xref:System.Nullable%601> 結構，是將 `null` \(Visual Basic 中的 `Nothing`\) 轉為其基礎類型，會擲回 <xref:System.InvalidOperationException> 例外狀況。  
  
###  <a name="BKMK_Causing_an_InvalidOperationException_with_an_invalid_cast"></a> 無效的轉換造成 InvalidOperationException  
 在這個方法中，Select 方法將 dbQueryResults 的 Null 元素轉換為 int 時，會擲回 <xref:System.InvalidOperationException>。  
  
 **例外狀況訊息：**  
  
-   其他資訊: 可為 Null 的物件必須具有值。  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults.Select(nullableInt => (int)nullableInt); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文內容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [將 Null 轉換成 T 的 Nullable&lt;T&gt;](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
###  <a name="BKMK_Avoiding_InvalidOperationException_from_a_bad_cast"></a> 從錯誤的轉換避免 InvalidOperationException  
 若要避免 <xref:System.InvalidOperationException>：  
  
-   使用 <xref:System.Nullable%601.HasValue%2A?displayProperty=fullName> 屬性，以選取那些不是 Null 的元素。  
  
-   使用其中一種多載的 <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> 方法，以提供預設值給 Null 元素。  
  
 **Nullable\<T\>.HasValue 範例**  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var ormMap = dbQueryResults .Where(nulllableInt => nulllableInt.HasValue) .Select(num => (int)num); //display map list foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); // handle nulls Console.WriteLine("{0} nulls encountered in dbQueryResults", dbQueryResults.Where(nullableInt => !nullableInt.HasValue).Count()); }  
```  
  
 **Nullable\<T\>.GetValueOrDefault 範例**  
  
 在這個範例中，我們使用 <xref:System.Nullable%601.GetValueOrDefault%28%600%29>，指定 `dbQueryResults` 所傳回之值預期值以外的預設值。  
  
```c#  
private void MapQueryResults() { var dbQueryResults = new int?[] { 1, 2, null, 4 }; var nullFlag = int.MinValue; var ormMap = dbQueryResults.Select(nullableInt => nullableInt.GetValueOrDefault(nullFlag)); // handle nulls Console.WriteLine("'{0}' indicates a null database value.", nullFlag); foreach (var num in ormMap) { Console.Write("{0} ", num); } Console.WriteLine(); }  
  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文內容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [將 Null 轉換成 T 的 Nullable&lt;T&gt;](#BKMK_A_Nullable_T_that_is_null_is_cast_to_T)  
  
##  <a name="BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection"></a> 在空集合上呼叫的 System.Linq.Enumerable 方法  
 <xref:System.Linq.Enumerable> 方法 <xref:System.Linq.Enumerable.Aggregate%2A>、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Last%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.First%2A>、<xref:System.Linq.Enumerable.Single%2A> 和 <xref:System.Linq.Enumerable.SingleOrDefault%2A> 會在某個序列上執行作業，並傳回單一結果。  
  
 序列若是空的，這些方法的某些多載會擲回 <xref:System.InvalidOperationException> 例外狀況；而其他多載會傳回 `null` \(Visual Basic 中的 `Nothing`\)。 若序列包含一個以上的元素，<xref:System.Linq.Enumerable.SingleOrDefault%2A> 也會擲回 <xref:System.InvalidOperationException>。  
  
> [!TIP]
>  本節中討論的大部分 <xref:System.Linq.Enumerable> 方法都是多載。 請確定您了解所選擇之多載的行為。  
  
 **例外狀況訊息：**  
  
 [Aggregate、Average、Last、Max 和 Min 方法](#BKMK_Aggregate_Average_Last_Max_and_Min_methods)  **&#124;**  [First 和 FirstOrDefault 方法](#BKMK_First_and_FirstOrDefault_methods)  **&#124;**  [Single 和 SingleOrDefault 方法](#BKMK_Single_and_SingleOrDefault_methods)  
  
###  <a name="BKMK_Aggregate_Average_Last_Max_and_Min_methods"></a> Aggregate、Average、Last、Max 和 Min 方法  
  
-   其他資訊: 序列未包含元素  
  
 **使用 Average 造成 InvalidOperationException**  
  
 在這個範例中，下列方法會在呼叫 <xref:System.InvalidOperationException> 方法時，擲回 <xref:System.Linq.Enumerable.Average%2A>，因為 Linq 運算式傳回序列，其中沒有包含大於 4 的元素。  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var avg = dbQueryResults.Where(num => num > 4).Average(); Console.WriteLine("The average value numbers greater than 4 in the returned records is {0}", avg); }  
```  
  
 當您使用這些方法之一，且沒有檢查空的序列時，便是隱含假設序列不是空的，而空的序列是未預期的元素。 當您假設序列不是空的，則捕捉或擲回例外狀況就很恰當。  
  
 **避免因空的序列造成 InvalidOperationException**  
  
 使用其中一種 <xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName> 方法，檢查序列是否是空的。  
  
> [!TIP]
>  如果 Average 的序列可能包含大量元素，或如果產生序列的作業是高度耗費資源，則使用 <xref:System.Linq.Enumerable.Any%2A> 可改善檢查的效能。  
  
```c#  
private void FindAverageOfNumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var moreThan4 = dbQueryResults.Where(num => num > 4); if(moreThan4.Any()) { var msgFormat = "The average value numbers greater than 4 in the returned records is {0}"; Console.WriteLine(msgFormat, moreThan4.Average()); } else { // handle empty collection Console.WriteLine("There are no values greater than 4 in the ecords."); } }  
  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文內容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [在空集合上呼叫的 System.Linq.Enumerable 方法](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_First_and_FirstOrDefault_methods"></a> First 和 FirstOrDefault 方法  
 <xref:System.Linq.Enumerable.First%2A> 會傳回序列中的第一個元素，或擲回<xref:System.InvalidOperationException> \(如果序列是空的\)。  您可以呼叫 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 方法，而不是<xref:System.Linq.Enumerable.First%2A>，以傳回指定或預設值，而不是擲回例外狀況。  
  
> [!NOTE]
>  在 .NET Framework 中，類型內含有預設值的概念。 例如，任何參考類型的預設值為 Null，整數類型則為零。 請參閱[預設值表](../Topic/Default%20Values%20Table%20\(C%23%20Reference\).md)  
  
 **使用 First 造成 InvalidOperationException**  
  
 <xref:System.Linq.Enumerable.First%2A> 是最佳化方法，會傳回序列中符合指定條件的第一個元素。 如果找不到滿足條件的元素，方法會擲回 <xref:System.InvalidOperationException> 例外狀況。  
  
 在這個範例中，`First` 方法會擲回例外狀況，因為 `dbQueryResults` 沒有包含大於 4 的元素。  
  
 **例外狀況訊息：**  
  
-   其他資訊: 序列未包含符合的元素  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; var firstNum = dbQueryResults.First(n=> n > 4); var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); }  
  
```  
  
 **使用 FirstOrDefault 避免例外狀況**  
  
 您可以使用其中一個 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 方法，取代 <xref:System.Linq.Enumerable.First%2A>，以檢查 `firstNum` 序列是否包含至少一個元素。 如果查詢中找不到滿足條件的元素，它會傳回指定值或預設值。 您可以檢查傳回的值，以判斷是否找到任何元素。  
  
> [!NOTE]
>  如果類型的預設值在序列中是有效的元素，使用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 可能會在實作上比較複雜。  
  
```c#  
private void FindANumbersGreaterThan4() { var dbQueryResults = new[] { 1, 2, 3, 4 }; // default(object) == null var firstNum = dbQueryResults.FirstOrDefault(n => n > 4); if (firstNum != 0) { var msgFormat = "{0} is an element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, firstNum); } else { // handle default case Console.WriteLine("No element of dbQueryResults is greater than 4."); } }  
  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文內容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [在空集合上呼叫的 System.Linq.Enumerable 方法](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
###  <a name="BKMK_Single_and_SingleOrDefault_methods"></a> Single 和 SingleOrDefault 方法  
 <xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName> 方法會傳回序列的唯一元素，或符合指定測試的序列中唯一元素。  
  
 如果序列中沒有任何元素，或序列中有一個以上的元素，方法會擲回 <xref:System.InvalidOperationException> 例外狀況。  
  
 當序列中沒有包含任何元素時，您可以使用 <xref:System.Linq.Enumerable.SingleOrDefault%2A>，傳回指定值或預設值，而不是擲回例外狀況。 不過，當序列包含一個以上符合選取述詞的元素時，<xref:System.Linq.Enumerable.SingleOrDefault%2A> 仍會擲回 <xref:System.InvalidOperationException>。  
  
> [!NOTE]
>  在 .NET Framework 中，類型內含有預設值的概念。 例如，任何參考類型的預設值為 Null，整數類型則為零。 請參閱[預設值表](../Topic/Default%20Values%20Table%20\(C%23%20Reference\).md)  
  
 **使用 Single 造成 InvalidOperationExceptions**  
  
 在這個範例中，`singleObject` 會擲回<xref:System.InvalidOperationException>，因為 `dbQueryResults` 沒有包含大於 4 的元素。  
  
 **例外狀況訊息：**  
  
-   其他資訊: 序列未包含符合的元素  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.Single(obj => (int)obj > 4); // display results var msgFormat = "{0} is the only element of dbQueryResults that is greater than 4"; Console.WriteLine(msgFormat, singleObject); }  
  
```  
  
 **使用 Single 或 SingleOrDefault 造成 InvalidOperationExceptions**  
  
 在這個範例中，`singleObject` 會擲回<xref:System.InvalidOperationException>，因為 `dbQueryResults` 包含一個以上大於 2 的元素。  
  
 **例外狀況訊息：**  
  
-   其他資訊: 序列包含一個以上相符的元素  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var singleObject = dbQueryResults.SingleOrDefault(obj => (int)obj > 2); if (singleObject != null) { var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, singleObject); } else { // handle empty collection Console.WriteLine("No element of dbQueryResults is greater than 2."); } }  
  
```  
  
 **使用 Single 避免 InvalidOperationExceptions**  
  
 使用 <xref:System.Linq.Enumerable.Single%2A> 和 <xref:System.Linq.Enumerable.SingleOrDefault%2A> 也可以做為您要的情況。<xref:System.Linq.Enumerable.Single%2A> 強烈意味著您需要從條件傳回只有一個結果。<xref:System.Linq.Enumerable.SingleOrDefault%2A> 會宣告您需要一個或零個結果，除此之外不要更多。 這些條件無效時，擲回或捕捉 <xref:System.InvalidOperationException> 就很恰當。 但是，如果您需要無效的條件以某些頻率發生，應該考慮使用其他 <xref:System.Linq.Enumerable> 方法，例如 <xref:System.Linq.Enumerable.First%2A> 或 <xref:System.Linq.Enumerable.Where%2A>，以產生您的結果。  
  
 在開發期間，您可以使用其中一個 <xref:System.Diagnostics.Debug.Assert%2A> 方法來檢查您的假設。 在這個範例中，強調顯示的程式碼會在開發期間導致偵錯工具中斷，並顯示判斷提示對話方塊。 判斷提示已在發行程式碼中移除，且如果結果無效，會擲回任何 <xref:System.Linq.Enumerable.Single%2A>。  
  
> [!NOTE]
>  使用 <xref:System.Linq.Enumerable.Take%2A>，並設定其 `count` 參數為 2，將傳回的序列限制為最多兩個元素。 此序列包括所有您需要檢查的情況 \(0、1 和 1 個以上的元素\)，而且當序列可能包含大量的元素，或產生序列的作業會高度耗費資源，也可改進檢查的效能。  
  
```c#  
private void FindTheOnlyNumberGreaterThan4() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan4 = dbQueryResults.Where(obj => (int)obj > 4).Take(2); System.Diagnostics.Debug.Assert(moreThan4.Count() == 1,String.Format("moreThan4.Count() == 1; Actual count: {0}", moreThan4.Count())); // do not handle exceptions in release code Console.WriteLine("{0} is the only element of dbQueryResults that is greater than 4", moreThan4.Single()); }  
  
```  
  
 如果您想要避免此例外狀況，同時處理發行程式碼中的無效狀態，可以修改上述的技巧。 在這個範例中，這個方法會回應 switch 陳述式中，`moreThan2` 所傳回的元素數目。  
  
```c#  
private void FindTheOnlyNumberGreaterThan2() { var dbQueryResults = new[] { (object)1, (object)2, (object)3, (object)4 }; var moreThan2 = dbQueryResults.TakeWhile(obj => (int)obj > 2).Take(2); switch(moreThan2.Count()) { case 1: // success var msgFormat = "{0} is the only element of dbQueryResults that is greater than 2"; Console.WriteLine(msgFormat, moreThan2.Single()); break; case 0: // handle empty collection Console.WriteLine("No element of the dbQueryResults are greater than 4."); break; default: // count > 1 // handle more than one element Console.WriteLine("More than one element of dbQueryResults is greater than 4"); break; } }  
  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文內容](#BKMK_In_this_article) ![In this section](../misc/media/pcs_backtotopmid.png "PCS\_BackToTopMid") [在空集合上呼叫的 System.Linq.Enumerable 方法](#BKMK_A_System_Linq_Enumerable_method_is_called_on_an_empty_collection)  
  
##  <a name="BKMK_Related_articles"></a> 相關文章  
 [例外狀況的設計方針 \(.NET Framework 設計方針\)](http://msdn.microsoft.com/library/ms229014)  
  
 [處理和擲回例外狀況 \(.NET Framework 應用程式基本功能\)](http://msdn.microsoft.com/library/5b2yeyab)  
  
 [如何：接收第一個可能發生的例外狀況通知 \(.NET Framework 開發指南\)](http://msdn.microsoft.com/library/Dd997368)  
  
 [如何：處理 PLINQ 查詢中的例外狀況 \(.NET Framework 開發指南\)](http://msdn.microsoft.com/library/Dd460712)  
  
 [Managed 執行緒中的例外狀況 \(.NET Framework 開發指南\)](http://msdn.microsoft.com/library/ms228965)  
  
 [例外狀況和例外處理 \(C\# 程式設計手冊\)](http://msdn.microsoft.com/library/ms173160)  
  
 [例外狀況處理陳述式 \(C\# 參考\)](http://msdn.microsoft.com/library/s7fekhdy)  
  
 [Try...Catch...Finally 陳述式 \(Visual Basic\)](http://msdn.microsoft.com/library/fk6t46tz)  
  
 [例外狀況處理 \(F\#\)](http://msdn.microsoft.com/library/Dd233223)  
  
 [C\+\+\/CLI 中的例外狀況](http://msdn.microsoft.com/library/Hh875008)  
  
 [例外狀況處理 \(工作平行程式庫\)](http://msdn.microsoft.com/library/Dd997415)  
  
 [例外狀況處理 \(偵錯\)](http://msdn.microsoft.com/library/x85tt0dd)  
  
 [逐步解說：處理並行例外狀況 \(在 Visual Studio 中存取資料\)](http://msdn.microsoft.com/library/ms171936)  
  
 [如何：處理資料繫結時所發生的錯誤和例外狀況 \(Windows Forms\)](http://msdn.microsoft.com/library/k26k86tb)  
  
 [處理網路應用程式中的例外狀況 \(XAML\) \(Windows\)](http://msdn.microsoft.com/library/Dn263240)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文內容](#BKMK_In_this_article)