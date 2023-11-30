Sub LinkCheckboxes()
    Dim ws As Worksheet
    Dim cb As CheckBox
    Dim i As Integer
    
    ' Set the worksheet
    Set ws = ThisWorkbook.Sheets("YourSheetName") ' Replace "YourSheetName" with the actual sheet name
    
    ' Loop through the checkboxes
    For i = 3 To 92 ' Adjust the range as needed
        ' Link each checkbox to the cell in column O
        Set cb = ws.CheckBoxes.Add(ws.Cells(i, 15).Left, ws.Cells(i, 15).Top, 50, 20) ' Column O is the 15th column
        cb.Name = "CheckBox" & i
        cb.LinkedCell = ws.Cells(i, 15).Address
    Next i
End Sub



