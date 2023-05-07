Download Link: https://assignmentchef.com/product/solved-lab-9-cmput-398
<br>
<h1>Objective</h1>

Implement a program that runs Radix sort on the GPU. The numbers given for sorting are integers from 0 to 65534

This lab will be submitted as one zipped file through <a href="https://eclass.srv.ualberta.ca/portal/">eclass</a><a href="https://eclass.srv.ualberta.ca/portal/">.</a> Details for submission are at the end of the lab.

<h1>Instructions</h1>

There are instructions on how to implement Radix sort at the following link: <a href="http://http.developer.nvidia.com/GPUGems3/gpugems3_ch39.html">http://http.developer.nvidia.com/GPUGems3/gpugems3_ch39.html</a>

If you want to read a more detailed version of Radix sort check out the following link:

<a href="http://mgarland.org/files/papers/nvr-2008-001.pdf">http://mgarland.org/files/papers/nvr-2008-001.pdf</a>

If you are unsure what Radix sort is then watch the following videos:

Radix Sort Algorithm <a href="https://www.youtube.com/watch?v=2109VzXVTus">https://www.youtube.com/watch?v=2109VzXVTus</a>

Radix Sort Part 1 – Intro to Parallel Programming <a href="https://www.youtube.com/watch?v=dPwAA7j-8o4">https://www.youtube.com/watch?v=dPwAA7j-8o4</a>

Radix Sort Part 2 – Intro to Parallel Programming <a href="https://www.youtube.com/watch?v=K-tNYzw8pm0">https://www.youtube.com/watch?v=K-tNYzw8pm0</a>

Radix Sort Part 3 – Intro to Parallel Programming <a href="https://www.youtube.com/watch?v=iS0S7F2U4-o">https://www.youtube.com/watch?v=iS0S7F2U4-o</a>

<h2>Instructions – Kernels</h2>

You will most likely have to implement at least three kernels; however, you can implement the Radix sort any way you want. The only restrictions are that it needs to be Radix sort written in CUDA and the calculations on the arrays must be performed on the GPU. Therefore, you shouldn’t be running the following kernels on the CPU:

<ul>

 <li>Calculate if a given bit is 0 or 1</li>

</ul>

Example given the following array return an array of 0 and 1. Everywhere the first bit is zero, least significant bit, return 1.

<ul>

 <li>Exclusive scan. This should be the same scan you implemented in the previous lab.</li>

 <li>This is emplaned in the GPU Gems 3 chapter 39.</li>

</ul>

<strong>Important: </strong>after launching a kernel make sure you call:

wbCheck(cudaDeviceSynchronize());

Or

cudaDeviceSynchronize();

<h2>Instructions – Pseudo Code</h2>

<ol>

 <li>FUNCTION Radix_Sort(output, input, len)</li>

 <li>Allocate memory if needed</li>

 <li>LOOP through bits 0 to 15</li>

 <li>Check bits</li>

 <li>Exclusive scan the checked bits</li>

 <li>Scatter the input array into the output</li>

 <li>END LOOP</li>

 <li>Free Allocated memory</li>

</ol>

It is probably a good idea if you scatter the input into the output. Then on every iteration the input becomes the output and the output becomes the input.

Iteration 1:

Input -&gt; Check bits -&gt; Scan Input -&gt; Scatter -&gt; Output

Iteration 2:

Output -&gt; Check bits -&gt; Scan

Output -&gt; Scatter -&gt; Input

Iteration 3:

Input -&gt; Check bits -&gt; Scan Input -&gt; Scatter -&gt; Output

Just make sure on the last iteration the sorted array is in the output array.

<h1>Local Setup Instructions</h1>

Steps:

<ol>

 <li>Download “Lab9.zip”.</li>

 <li>Unzip the file.</li>

 <li>Open the Visual Studios Solution in Visual Studios 2013.</li>

 <li>Build the project. Note the project has two configurations.

  <ol>

   <li>Debug</li>

   <li>Submission</li>

  </ol></li>

</ol>

But make sure you have the “Submission” configuration selected when you finally submit.

<ol start="5">

 <li>Run the program by pressing the following button:</li>

</ol>

Make sure the “Debug” configuration is selected. Running the program in Visual Studios will run one of the tests located in “Dataset /Test”.

<h1>Testing</h1>

To run all tests located in “Dataset/ Test”, first build the project with the “Submission” configuration selected. Make sure you see the “Submission” folder and the folder contains the executables.

To run the tests, click on “Testing_Script.bat”. This will take a couple of seconds to run and the terminal should close when finished. The output is saved in “Marks.js”, but to view the calculated grade open “Grade.html” in a browser. If you make changes and rerun the tests, then make sure you reload “Grade.html”. You can double check with the timestamp at the top of the page.