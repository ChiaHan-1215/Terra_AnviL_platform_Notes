# Related notes for construction/working wiht wdl script

### the "~" meaning 
When you use `~{File_variable}` within a command block, WDL will automatically quote the path of the File_variable when it's passed to the underlying shell command. 

```wdl
task process_file {
  input {
    File input_data
  }
  command <<<
    my_tool --input ~{input_data} --output output.txt
  >>>
  output {
    File processed_output = "output.txt"
  }
}

```
will gives 

```wdl
my_tool --input "my data.txt" --output output.txt
```
so that the variable won't be "my" and "data.txt" 
