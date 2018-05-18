

## Entry Point

* `/src/cli/cli.c` 是進入 interactive mode，這個檔案唯一有 main function，大約 102 行
	
```c
    int main(int argc, char *argv[]) {
        int retval = EXIT_SUCCESS;

        memset(&cli, 0, sizeof(cli));

        /*
          ↪ sjs
          Skookum JS 17.0.0alpha running on osx x64
          [Engine: Duktape v2.2.0 (a459cf3)]
          [Build: Debug on 2018-05-18T11:28:25Z]
          [Clang 9.0.0.9000039 on Darwin-16.7.0]
          sjs> 你好       # "你好" 在我按下 Enter 才出現
          = undefined
         */        
        fprintf(stdout, "你好");

         ...
    }
```    


* `/src/platform/darwin.c` 是用來做 `sjs hello.js` 這個的 (mac OS platform)，這檔案沒有 main function，只有 30 行 (Linux)

```c

void sjs__executable(char* buf, size_t size) {

		/*
			↪ sjs examples/hello.js
			你好
			What is your name? Veck
			Hello Veck, nice to meet you!
		*/

    fprintf(stdout, "你好\n");

    ...
}    
```

## Compile and Install

修改完存擋後，輸入 `make & make install` 就可以編譯並且完成安裝，安裝完當然就可以直接開始測試了！
