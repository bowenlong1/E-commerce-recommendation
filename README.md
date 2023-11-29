Sub Worksheet_SelectionChange(ByVal Target As Range)
    Dim selectedRange As Range
    Dim sumSelected As Double
    
    ' Define the range of selected cells
    On Error Resume Next
    Set selectedRange = Intersect(Target, Range("Table1"))
    On Error GoTo 0

    ' If cells within the data range are selected, calculate the sum
    If Not selectedRange Is Nothing Then
        sumSelected = WorksheetFunction.Sum(selectedRange)
        
        ' Display the sum in the status bar
        Application.StatusBar = "Selected Sum: " & sumSelected & "   Percentage: " & Format(sumSelected / 34001, "0.00%")
    Else
        ' Clear the status bar if no cells are selected
        Application.StatusBar = False
    End If
End Sub
