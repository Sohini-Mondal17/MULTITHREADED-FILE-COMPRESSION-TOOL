# MULTITHREADED-FILE-COMPRESSION-TOOL

*COMPANY*: CODTECH IT SOLUTIONS

*NAME*: SOHINI MONDAL

*INTERN ID*: CT04DM429

*DOMAIN*: C++ PROGRAMMING

*DURATION*: 4 WEEKS

*MENTOR*: NELLA SANTOSH KUMAR

*DESCRIPTION*:The provided C++ program implements a Run-Length Encoding (RLE) compression and decompression system using both single-threaded and multithreaded approaches to improve performance when processing large text files. RLE is a basic compression technique where consecutive repeating characters are replaced by a single character followed by its frequency count. This program emphasizes multithreaded file processing, performance comparison, and validation to ensure the integrity of decompressed output.

At the core of the program are two functions: rleCompress and rleDecompress. The rleCompress function iterates over a string, identifying sequences of identical characters, and encodes them using the character followed by its count (limited to 255 to fit in one byte). The rleDecompress function does the reverse, converting each character-count pair back into the original sequence by repeating the character as many times as specified by its count. The compressed format assumes each pair of bytes represents one character and its count, making decompression straightforward but sensitive to formatting—if the compressed data size is odd, it throws an error.

The main performance-oriented function, processFile, handles multithreaded processing. It reads the entire input file into a string, divides the data into roughly equal chunks based on the specified number of threads, and spawns a thread for each chunk. To avoid corrupting RLE sequences, threads skip over characters that might split a sequence at the chunk boundary. Each thread either compresses or decompresses its chunk and stores the result in a shared vector. After all threads finish, the main thread combines the results and writes them sequentially to the output file. Timing is recorded using high-resolution clocks to display how long the operation takes.

The program also provides a single-threaded version of file processing through the processFileSingleThread function. This method performs compression or decompression sequentially in one thread and is useful for performance comparison. The user can observe the difference in time taken between the single-threaded and multithreaded methods, demonstrating how threading can optimize processing on multi-core systems.

To verify correctness, the validateFiles function compares the content of the original input file with the decompressed output file. If the contents are identical, it confirms the accuracy of compression and decompression; otherwise, it prints the sizes of both files and indicates a mismatch.

The main function orchestrates the program’s execution. It first creates a large test file containing many lines with repeated characters to demonstrate the effectiveness of RLE. It then performs single-threaded compression and decompression, followed by multithreaded operations using four threads. After each method, validation is performed to ensure the decompressed file matches the original.

Overall, the program effectively demonstrates how RLE compression can be optimized using multithreading. It ensures thread safety, accurate chunk division, and correctness of output while also benchmarking the benefits of concurrent processing. This approach is particularly suitable for large datasets where performance is a key concern.

*OUTPUT*:

