---
title: "疑難排解例外狀況：System.NullReferenceException | Microsoft Docs"
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
  - "NullReferenceException 類別"
ms.assetid: 4822b0b4-8105-43fb-887a-3cc51ff02899
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.NullReferenceException
當您嘗試使用值為 <xref:System.NullReferenceException> 的*「參考類型」*\(reference type\) \([C\#](../Topic/Reference%20Types%20\(C%23%20Reference\).md)、[Visual Basic](../Topic/Value%20Types%20and%20Reference%20Types.md)\) 時，會發生 `null`。 例如，您可能未先使用 [new](../Topic/new%20\(C%23%20Reference\).md) 關鍵字 \(在 Visual Basic 中為 [New](../Topic/New%20Operator%20\(Visual%20Basic\).md)\)，就嘗試使用物件，或是嘗試使用值已設為 [null](../Topic/null%20\(C%23%20Reference\).md) \(在 Visual Basic 中為 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)\) 的物件。  
  
##  <a name="BKMK_Contents"></a> 本文章節  
 [在本文中使用的類別](#BKMK_Classes_used_in_the_examples)  
  
 [NullReferenceExceptions 的常見原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 [在開發期間尋找 null 參考例外狀況的來源](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 [避免 NullReferenceExceptions](#BKMK_Avoid_NullReferenceExceptions)  
  
 [在發行程式碼中處理 NullReferenceException](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
##  <a name="BKMK_Classes_used_in_the_examples"></a> 在本文中使用的類別  
 本文中大部分的範例都會使用下列其中一個類別，或兩者都使用：  
  
```c#  
public class Automobile { public EngineInfo Engine {get; set;} } public class EngineInfo { public EngineInfo() { } public EngineInfo(string powerSrc, double engineSize) { Power = powerSrc; Size = engineSize; } public double Size { get; set; } public string Power = null; }  
  
```  
  
```vb  
Public Class Automobile Public Property Engine As EngineInfo End Class Public Class EngineInfo Public Sub New() End Sub Public Sub New(powerSrc As String, engineSize As Double) Power = powerSrc Size = engineSize End Sub Public Property Size() As Double Public Power As String = Nothing End Class  
  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
##  <a name="BKMK_Common_causes_of_NullReferenceExceptions"></a> NullReferenceExceptions 的常見原因  
 任何參考類型變數都可以是 null。 區域變數、類別的屬性、方法參數和方法傳回值都可以包含 null 參考。 當這些變數的方法或屬性為 null 時，如果加以呼叫，就會導致 NullReferenceException。 特殊情況：  
  
 [區域變數或成員欄位已宣告但未初始化](#BKMK_A_local_variable_or_member_field_is_declared_but_not_initialized)  
  
 [設為 null 的屬性或欄位](#BKMK_A_property_or_field_is_null)  
  
 [方法參數為 null](#BKMK_A_method_parameter_is_null)  
  
 [方法的傳回值為 null](#BKMK_The_return_value_of_a_method_is_null)  
  
 [集合或陣列中的物件為 null](#BKMK_An_object_in_a_collection_or_array_is_null)  
  
 [因為某條件而未建立物件](#BKMK_An_object_is_not_created_because_of_a_condition)  
  
 [由參考傳遞至方法的物件設為 null](#BKMK_An_object_passed_by_reference_to_a_method_is_set_to_null)  
  
###  <a name="BKMK_A_local_variable_or_member_field_is_declared_but_not_initialized"></a> 區域變數或成員欄位已宣告但未初始化  
 Visual Basic 程式碼最常發生這個簡單的錯誤。 除了宣告要當作輸出參數傳遞的變數之外，C\# 編譯器不允許使用區域參考變數，除非其有初始化。 Visual Basic 編譯器會產生警告。  
  
-   在下列 C\# 程式碼中，強調顯示的行會產生這個編譯器錯誤：  
  
 **使用未指派的區域變數 'engine'**  
  
-   在 Visual Basic 程式碼中，強調顯示的行會產生編譯器警告 BC42104：  
  
 **變數 'engine' 已在指派值之前使用。 在執行階段可能會產生 null 參考例外狀況。**     而當該行執行時，的確會擲回 NullReferenceException。  
  
```c#  
public void NullReferencFromUninitializedLocalVariable() { EngineInfo engine; Console.WriteLine(engine.ToString()); }  
```  
  
```vb  
Public Sub NullReferencFromUninitializedLocalVariable() Dim engine As EngineInfo Console.WriteLine(engine.ToString()) End Sub  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常見原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
###  <a name="BKMK_A_property_or_field_is_null"></a> 設為 null 的屬性或欄位  
 建立類別之後，類別的欄位和屬性會自動初始化為其[預設值](../Topic/Data%20Member%20Default%20Values.md)。 參考類型的預設值為 `null` \(在 Visual Basic 中為 `Nothing`\)。當欄位或屬性值為 null 時，在父類別的欄位或屬性上呼叫成員方法會導致 NullReferenceException。  
  
 在此範例中，反白顯示的行會擲回 NullReferenceException，因為 `Engine` 的 `car` 屬性會自動初始化為 null。  
  
```c#  
public void NullReferenceFromProperty() { var car = new Automobile(); Console.WriteLine(car.Engine.ToString()); }  
```  
  
```vb  
Public Sub NullReferenceFromProperty() Dim car = New Automobile() Console.WriteLine(car.Engine.ToString()) End Sub  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常見原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
###  <a name="BKMK_A_method_parameter_is_null"></a> 方法參數為 null  
 參考類型的方法參數可以是 `null` \(在 Visual Basic 中為 `Nothing`\)。 當參數值為 null 時，呼叫成員方法或屬性會導致 NullReferenceException。  
  
 在此範例中，反白顯示的行會擲回 NullReferenceException，因為 `BadEngineInfoPassedToMethod` 使用參數值 null 來呼叫 `NullReferenceFromMethodParameter`。  
  
```c  
public void BadEngineInfoPassedToMethod() { EngineInfo eng = null; NullReferenceFromMethodParameter(eng); } public void NullReferenceFromMethodParameter(EngineInfo engine) { Console.WriteLine(engine.ToString()); }  
  
```  
  
```vb  
Public Sub BadParameterPassedToMethod() As EngineInfo Dim eng As EngineInfo = Nothing NullReferenceFromMethodParameter(eng) End Sub Public Sub NullReferenceFromMethodParameter(engine As EngineInfo) Console.WriteLine(engine.ToString()) End Sub  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常見原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
###  <a name="BKMK_The_return_value_of_a_method_is_null"></a> 方法的傳回值為 null  
 傳回參考類型的方法會傳回 `null` \(在 Visual Basic 中為 `Nothing`\)。 當參考為 null 時，呼叫傳回之參考類型的方法或屬性會導致 NullReferenceException。  
  
 在此範例中，強調顯示的行會擲回 NullReferenceException，因為呼叫 `BadGetEngineInfo` 會傳回 `NullReferenceFromMethodParameter` 方法中的 null 參考。  
  
```c#  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } public void NullReferenceFromMethodReturnValue() { var engine = BadGetEngineInfo(); Console.WriteLine(engine.ToString()); }  
```  
  
```vb  
Public Function BadGetEngineInfo() As EngineInfo Dim engine As EngineInfo = Nothing Return engine End Function Public Sub NullReferenceFromMethodReturnValue() Dim engine = BadGetEngineInfo() Console.WriteLine(engine.ToString()) End Sub  
  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常見原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_in_a_collection_or_array_is_null"></a> 集合或陣列中的物件為 null  
 參考類型的清單或陣列可能會包含 null 項目。 呼叫 null 清單項目的方法或屬性會導致 NullReferenceException。  
  
 在此範例中，`NullReferenceFromListItem()` 中反白顯示的行會擲回 NullReferenceException，因為呼叫 `BadGetCarList` 會傳回 null 項目。  
  
```c#  
public Automobile[] BadGetCarList() { var autos = new Automobile[10]; for (int i = 0; i autos.Length; i++) { if (i != 6) { autos[i] = new Automobile(); } } return autos; } public void NullReferenceFromListItem() { var cars = BadGetCarList(); foreach (Automobile car in cars) { Console.WriteLine(car.ToString()); } }  
```  
  
```vb  
Public Function BadGetCarList() As Automobile() Dim autos = New Automobile(10) {} For i As Integer = 0 To 9 If i <> 6 Then autos(i) = New Automobile() End If Next Return autos End Function Public Sub NullReferenceFromListItem() Dim cars = BadGetCarList() For Each car As Automobile In cars Console.WriteLine(car.ToString()) Next End Sub  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常見原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_is_not_created_because_of_a_condition"></a> 因為某條件而未建立物件  
 如果在條件性區塊中初始化參考類型，當條件為 false 時，就不會建立物件。  
  
 在此範例中，`NullReferenceFromConditionalCreation` 中強調顯示的行會擲回 NullReferenceException，因為唯有當 `engine` 方法傳回 `DetermineTheCondition()` 時，才會初始化 `true` 變數。  
  
```c#  
public bool DetermineTheCondition() { return false; } public void NullReferenceFromConditionalCreation() { EngineInfo engine = null; var condition = DetermineTheCondition(); if (condition) { engine = new EngineInfo(); engine.Power = "Diesel"; engine.Size = 2.4; } Console.WriteLine(engine.Size); }  
```  
  
```vb  
Public Function DetermineTheCondition() As Boolean Return False End Function Public Sub NullReferenceFromConditionalCreation() Dim engine As EngineInfo = Nothing Dim condition = DetermineTheCondition() If condition Then engine = New EngineInfo() engine.Power = "Diesel" engine.Size = 2.4 End If Console.WriteLine(engine.Size) End Sub  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常見原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
### 傳遞至方法的物件屬性設為 null  
 以值將物件當作參數傳遞至方法時 \(在 C\# 中未使用 `ref` 或 `out` 關鍵字，或在 Visual Basic 中未使用 `ByRef` 關鍵字\)，該方法無法變更參數的記憶體位置 \(參數指向的位置\)，但可以變更物件的屬性。  
  
 在此範例中，`NullPropertyReferenceFromPassToMethod` 方法會建立 `Automobile` 物件，並初始化 `Engine` 屬性。 然後會呼叫 `BadSwapCarEngine`，將新物件當作參數傳遞。`BadSwapCarEngine` 將 Engine 屬性設為 null，這會導致 `NullPropertyReferenceFromPassToMethod` 中反白顯示的行擲回 NullReferenceException。  
  
```c#  
public void BadSwapCarEngine(Automobile car) { car.Engine = null; } public void (Automobile car) { car.Engine = new EngineInfo("GAS", 1.5); BadSwapCarEngine(car); Console.WriteLine(car.Engine.ToString()); }  
  
```  
  
```vb  
Public Sub BadSwapCarEngine(car As Automobile) car.Engine = Nothing End Sub Public Sub NullPropertyReferenceFromPassToMethod() Dim car As New Automobile() car.Engine = New EngineInfo("GAS", 1.5) BadSwapCarEngine(car) Console.WriteLine(car.Engine.ToString()) End Sub  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常見原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
###  <a name="BKMK_An_object_passed_by_reference_to_a_method_is_set_to_null"></a> 由參考傳遞至方法的物件設為 null  
 當您以參考將參考類型當作參數傳遞至方法時 \(在 C\# 中使用 `ref` 或 `out` 關鍵字，或在 Visual Basic 中使用 `ByRef` 關鍵字\)，可以變更參數指向的記憶體位置。  
  
 當您以參考將參考類型傳遞至方法時，該方法可將參考的類型設為 `null` \(在 Visual Basic 中為`Nothing`\)。  
  
 在此範例中，`NullReferenceFromPassToMethodByRef` 中強調顯示的行會擲回 NullReferenceExceptions，因為呼叫 `BadEngineSwapByRef` 方法會將 `stockEngine` 變數設為 null。  
  
```c#  
public void BadEngineSwapByRef(ref EngineInfo engine) { engine = null; } public void NullReferenceFromPassToMethodByRef() { var stockEngine = new EngineInfo(); stockEngine.Power = "Gas"; stockEngine.Size = 7.0; BadSwapEngineByRef(ref stockEngine); Console.WriteLine(stockEngine.ToString()); }  
```  
  
```vb  
Public Sub BadSwapEngineByRef(ByRef engine As EngineInfo) engine = Nothing End Sub Public Sub NullReferenceFromPassToMethodByRef() Dim formatStr = "The stock engine has been replaced by a {0} liter {} engine" Dim stockEngine = New EngineInfo() stockEngine.Power = "Gas" stockEngine.Size = 7.0 BadSwapEngineByRef(stockEngine) Console.WriteLine(stockEngine.ToString()) End Sub  
  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [NullReferenceExceptions 的常見原因](#BKMK_Common_causes_of_NullReferenceExceptions)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_of_a_null_reference_exception_during_development"></a> 在開發期間尋找 null 參考例外狀況的來源  
 [使用資料提示、[區域變數] 視窗和監看式視窗來查看變數值](#BKMK_Use_data_tips_the_Locals_window_and_watch_windows_to_see_variables_values)  
  
 [查看呼叫堆疊，尋找參考變數未初始化或設為 null 的地方](#BKMK_Walk_the_call_stack_to_find_where_a_type_reference_is_not_initialized_or_set_to_null_)  
  
 [將條件中斷點設為當物件為 null (在 Visual Basic 中為 Nothing) 時，停止偵錯](#BKMK_Set_conditional_breakpoints_to_stop_debugging_when_an_object_is_null_Nothing_in_Visual_Basic_)  
  
###  <a name="BKMK_Use_data_tips_the_Locals_window_and_watch_windows_to_see_variables_values"></a> 使用資料提示、\[區域變數\] 視窗和監看式視窗來查看變數值  
  
-   將游標重新置於變數名稱上，可在[資料提示](../Topic/View%20data%20values%20in%20Data%20Tips%20%20in%20the%20code%20editor.md)中查看其值。 如果變數參考物件或集合，您可以展開資料類型來查看其屬性或項目。  
  
-   開啟 \[區域變數\] 視窗，以查看目前內容裡所有作用中的變數。  
  
-   使用[監看式視窗](../Topic/Watch%20and%20QuickWatch%20Windows.md)，當您逐步執行程式碼時，專注於變數如何變化。  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [在開發期間尋找 null 參考例外狀況的來源](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
###  <a name="BKMK_Walk_the_call_stack_to_find_where_a_type_reference_is_not_initialized_or_set_to_null_"></a> 查看呼叫堆疊，尋找參考變數未初始化或設為 null 的地方  
 Visual Studio 的[呼叫堆疊視窗](../Topic/How%20to:%20Use%20the%20Call%20Stack%20Window.md)會顯示偵錯工具停止於例外狀況或中斷點時，未完成之方法的名稱清單。 您可以在 \[呼叫堆疊\] 視窗中選取名稱，並選擇 \[切換至框架\]，以將執行內容變更為方法，並檢查其變數。  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [在開發期間尋找 null 參考例外狀況的來源](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
###  <a name="BKMK_Set_conditional_breakpoints_to_stop_debugging_when_an_object_is_null_Nothing_in_Visual_Basic_"></a> 將條件中斷點設為當物件為 null \(在 Visual Basic 中為 Nothing\) 時，停止偵錯  
 您可以設定要在變數為 Null 時中斷的[條件中斷點](http://msdn.microsoft.com/library/5557y8b4.aspx#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)。 如果 null 參考不常出現 \(例如當集合中的項目偶爾為 null 時\)，條件中斷點會很有幫助。 使用條件中斷點的另一個好處，就是可讓您在認可至特定處理常式之前，進行問題偵錯。  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [在開發期間尋找 null 參考例外狀況的來源](#BKMK_Find_the_source_of_a_null_reference_exception_during_development)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
##  <a name="BKMK_Avoid_NullReferenceExceptions"></a> 避免 NullReferenceExceptions  
 [使用 Debug.Assert 來確認不區分](#BKMK_Use_Debug_Assert_to_confirm_an_invariant)  
  
 [完全初始化參考類型](#BKMK_Fully_initialize_reference_types)  
  
###  <a name="BKMK_Use_Debug_Assert_to_confirm_an_invariant"></a> 使用 Debug.Assert 來確認不區分  
 *「不區分」*\(invariant\) 是您確定為 true 的條件。 只會從您的應用程式偵錯組建來呼叫 [Debug.Assert \(System.Diagnostics\)](http://msdn.microsoft.com/library/system.diagnostics.debug.assert.aspx) 陳述式，而不會從發行程式碼來呼叫。 如果不區分條件不是 true，則偵錯工具會在 Assert 陳述式中斷，並顯示對話方塊。`Debug.Assert` 可檢查您在開發應用程式時，條件並未變更。 判斷提示也會為讀取您程式碼的其他人記錄條件必須永遠是 true。  
  
 例如，`MakeEngineFaster` 方法會假設其 `engine` 參數永遠都不會是 null，因為已知其唯一的呼叫端方法 \(`TheOnlyCallerOfMakeEngineFaster`\) 會完全初始化 `EngineInfo`。`MakeEngineFaster` 中的判斷提示會記錄這個假設，並檢查該假設為 true。  
  
 若有人加入不會初始化參數的新呼叫端方法 \(`BadNewCallerOfMakeEngineFaster`\)，就會觸發判斷提示。  
  
```c#  
private void TheOnlyCallerOfMakeEngineFaster() { var engine = new EngineInfo(); engine.Power = "GAS"; engine.Size = 1.5; MakeEngineFaster(engine); } private void MakeEngineFaster(EngineInfo engine) { System.Diagnostics.Debug.Assert(engine != null, "Assert: engine != null"); engine.Size *= 2; Console.WriteLine("The engine is twice as fast"); } private void BadNewCallerOfMakeEngineFaster() { EngineInfo engine = null; MakeEngineFaster(engine); }  
```  
  
```vb  
Public Sub TheOnlyCallerOfMakeEngineFaster() Dim engine As New EngineInfo engine.Power = "GAS" engine.Size = 1.5 MakeEngineFaster(engine) End Sub Private Sub MakeEngineFaster(engine As EngineInfo) System.Diagnostics.Debug.Assert(engine IsNot Nothing, "Assert: engine IsNot Nothing") engine.Size = engine.Size * 2 Console.WriteLine("The engine is twice as fast") End Sub Public Sub BadNewCallerOfMakeEngineFaster() Dim engine As EngineInfo = Nothing MakeEngineFaster(engine) End Sub  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [避免 NullReferenceExceptions](#BKMK_Avoid_NullReferenceExceptions)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
###  <a name="BKMK_Fully_initialize_reference_types"></a> 完全初始化參考類型  
 若要避免許多 NullReferenceExceptions，請盡可能在接近建立參考類型的時候，將其完全初始化。  
  
 **將完全初始化加入您自己的類別**  
  
 如果您要控制擲回 NullReferenceException 的類別，請考慮在類型的建構函式中完全初始化物件。 例如，這裡有一個修訂過的範例類別版本，可保證完全初始化：  
  
```c#  
public class Automobile { public EngineInfo Engine { get; set; } public Automobile(){this.Engine = new EngineInfo();} public Automobile(string powerSrc, double engineSize) { this.Engine = new EngineInfo(powerSrc, engineSize); } } public class EngineInfo { public double Size {get; set;} public string Power {get; set;} public EngineInfo(){// the base enginethis.Power = "GAS";this.Size = 1.5;} public EngineInfo(string powerSrc, double engineSize) { this.Power = powerSrc; this.Size = engineSize; } }  
  
```  
  
```vb  
Public Class Automobile Public Property Engine As EngineInfo     Public Sub New()Me.Engine = New EngineInfo()End SubPublic Sub New(powerSrc As String, engineSize As Double)Me.Engine = New EngineInfo(powerSrc, engineSize)End Sub End Class Public Class BaseEngineInfo Public Sub New()' the base engineMe.Power = "GAS"Me.Size = 1.5End Sub Public Sub New(powerSrc As String, engineSize As Double) Power = powerSrc Size = engineSize End Sub Public Property Size() As Double Public Power As String = String.Empty End Class  
```  
  
> [!NOTE]
>  **針對大型或不常使用的屬性，使用延遲初始設定**  
>   
>  若要減少類別的記憶體使用量，並提升其效能，請考慮使用參考類型屬性的延遲初始設定。 請參閱 [延遲初始設定](../Topic/Lazy%20Initialization.md)。  
  
##  <a name="BKMK_Handle_NullReferenceExceptions_in_release_code"></a> 在發行程式碼中處理 NullReferenceException  
 [在使用參考類型之前，先檢查是否有 null (在 Visual Basic 中為 Nothing)](#BKMK_Check_for_null_Nothing_in_Visual_Basic_before_using_a_reference_type)  
  
 [使用 try-catch-finally (在 Visual Basic 中為 Try-Catch-Finally) 來處理例外狀況](#BKMK_Use_try_catch_finally_Try_Catch_Finally_in_Visual_Basic_to_handle_the_exception)  
  
 最好是能夠避免 NullReferenceException，而不是發生後再來處理。 處理例外狀況會讓您的程式碼更難維護及了解，而且有時候會引進其他 Bug。 NullReferenceException 通常是無法修復的錯誤。 在這些案例中，讓例外狀況停止應用程式可能是最好的替代方案。  
  
 不過，有許多情況中處理錯誤會有幫助。  
  
-   您的應用程式可以忽略 null 的物件。 例如，如果您的應用程式會擷取並處理資料庫中的記錄，也許您可以忽略某些會產生 null 物件的錯誤記錄。 將錯誤資料記錄在記錄檔或應用程式 UI 中可能是您唯一必須做的事。  
  
-   您可以從例外狀況復原。 例如，連接中斷或逾時，如果呼叫會傳回參考類型的 Web 服務可能會傳回 null。 您可以嘗試重新建立連接，並試著再呼叫一次。  
  
-   您可以將應用程式的狀態還原至有效狀態。 例如，您執行的多步驟工作可能會需要您先將資訊儲存至資料儲存區，才能呼叫擲回 NullReferenceException 的方法。 如果未初始化的物件會損毀資料記錄，您可以先移除之前的資料再關閉應用程式。  
  
-   您想要回報該例外狀況。 例如，如果錯誤由應用程式使用者的錯誤所造成，您可以產生訊息來幫助他提供正確的資訊。 您也可以記錄錯誤的資訊，以幫助您修正問題。 有些架構，像 ASP.NET，具有高層級且可以擷取所有錯誤的例外狀況處理常式，此時應用程式永遠不會損毀，在這種情況下，記錄例外狀況可能是您可以知道它有發生的唯一方法。  
  
 以下有兩個在發行程式碼中處理 NullReferenceException 的方式。  
  
###  <a name="BKMK_Check_for_null_Nothing_in_Visual_Basic_before_using_a_reference_type"></a> 在使用參考類型之前，先檢查是否有 null \(在 Visual Basic 中為 Nothing\)  
 在使用物件之前，先使用明確測試來檢查是否有 null，可以避免 try\-catch\-finally 建構的效能負面影響。 不過，您還是必須決定並實作用來回應未初始化物件的方法。  
  
 在這個範例中，`CheckForNullReferenceFromMethodReturnValue` 會測試 `BadGetEngineInfo` 方法的傳回值。 如果物件不是 null，就會加以使用，否則該方法會回報錯誤。  
  
```c#  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } public void CheckForNullReferenceFromMethodReturnValue() { var engine = BadGetEngineInfo(); if(engine != null) { // modify the info engine.Power = "DIESEL"; engine.Size = 2.4; } else { // report the error Console.WriteLine("BadGetEngine returned null") } }  
  
```  
  
```vb  
public EngineInfo BadGetEngineInfo() { EngineInfo engine = null; return engine; } Public Sub CheckForNullReferenceFromMethodReturnValue() Dim engine = BadGetEngineInfo() If (engine IsNot Nothing) Then ' modify the info engine.Power = "DIESEL" engine.Size = 2.4 Else ' report the error Console.WriteLine("BadGetEngineInfo returned Nothing") End If End Sub  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [在發行程式碼中處理 NullReferenceException](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
###  <a name="BKMK_Use_try_catch_finally_Try_Catch_Finally_in_Visual_Basic_to_handle_the_exception"></a> 使用 try\-catch\-finally \(在 Visual Basic 中為 Try\-Catch\-Finally\) 來處理例外狀況  
 與其檢查物件是否為 null，使用內建的例外狀況處理建構 \(在 C\# 為 [try、catch、finally](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md)，在 Visual Basic 中為 [Try、Catch、Finally](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)\) 可提供您更多的選項來處理 NullReferenceException。  
  
 在此範例中，`CatchNullReferenceFromMethodCall` 使用兩個判斷提示來確認其參數包含完整 automobile \(包括 engine\) 的假設。 在 `try` 區塊中，強調顯示的行會擲回 NullReferenceException，因為呼叫 `RarelyBadEngineSwap` 會損毀 car 的 `Engine` 屬性。`catch` 區塊會擷取例外狀況、將例外狀況資訊寫入檔案中，並且向使用者回報錯誤。 在 `finally` 區塊中，該方法會確保 car 的狀態不會比方法開始之後更糟。  
  
```c#  
public void RarelyBadSwapCarEngine(Automobile car) { if ((new Random()).Next() == 42) { car.Engine = null; } else { car.Engine = new EngineInfo("DIESEL", 2.4); } } public void CatchNullReferenceFromMethodCall(Automobile car) { System.Diagnostics.Debug.Assert(car != null, "Assert: car != null"); System.Diagnostics.Debug.Assert(car.Engine != null, "Assert: car.Engine != null"); // save current engine properties in case they're needed var enginePowerBefore = car.Engine.Power; var engineSizeBefore = car.Engine.Size; try { RarelyBadSwapCarEngine(car); var msg = "Swap succeeded. New engine power source: {0} size {1}"; Console.WriteLine(msg, car.Engine.Power, car.Engine.Size); } catch(NullReferenceException nullRefEx) { // write exception info to log file LogException(nullRefEx); // notify the user Console.WriteLine("Engine swap failed. Please call your customer rep."); } finally { if(car.Engine == null) { car.Engine = new EngineInfo(enginePowerBefore, engineSizeBefore); } } }  
  
```  
  
```vb  
Public Sub RarelyBadSwapCarEngine(car As Automobile) If (New Random()).Next = 42 Then car.Engine = Nothing Else car.Engine = New EngineInfo("DIESEL", 2.4) End If End Sub Public Sub CatchNullReferenceFromMethodCall(car As Automobile) System.Diagnostics.Debug.Assert(car IsNot Nothing) System.Diagnostics.Debug.Assert(car.Engine IsNot Nothing) ' save current engine properties in case they're needed Dim powerBefore = car.Engine.Power Dim sizeBefore = car.Engine.Size Try RarelyBadSwapCarEngine(car) Dim msg = "Swap succeeded. New engine power source: {0} size {1}" Console.WriteLine(msg, car.Engine.Power, car.Engine.Size) Catch nullRefEx As NullReferenceException ' write exception info to log file LogException(nullRefEx) ' notify user Console.WriteLine("Engine swap failed. Please call your customer rep.") Finally If car.Engine Is Nothing Then car.Engine = New EngineInfo(powerBefore, sizeBefore) End Try End Sub  
  
```  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [在發行程式碼中處理 NullReferenceException](#BKMK_Handle_NullReferenceExceptions_in_release_code)  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)  
  
## 相關文章  
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
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [本文章節](#BKMK_Contents)