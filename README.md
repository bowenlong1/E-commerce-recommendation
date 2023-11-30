Sub LinkCheckboxesAndFormat()
    Dim ws As Worksheet
    Dim cb As CheckBox
    Dim i As Integer
    Dim leftPosition As Double
    Dim topPosition As Double
    
    ' Set the worksheet
    Set ws = ThisWorkbook.Sheets("YourSheetName") ' Replace "YourSheetName" with the actual sheet name
    
    ' Loop through the checkboxes
    For i = 3 To 92 ' Adjust the range as needed
        ' Set position for each checkbox
        leftPosition = ws.Cells(i, 15).Left ' Column O is the 15th column
        topPosition = ws.Cells(i, 15).Top + 5 ' Add 5 for a little formatting
        
        ' Create checkboxes in columns O to T
        For j = 0 To 5
            Set cb = ws.CheckBoxes.Add(leftPosition + (j * 60), topPosition, 50, 20)
            
            ' Link each checkbox to the corresponding cell in columns O to T
            cb.LinkedCell = ws.Cells(i, 15 + j).Address
            
            ' Customize checkbox appearance
            cb.Text = "" ' Remove default text
        Next j
    Next i
End Sub



