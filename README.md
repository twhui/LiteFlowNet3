# LiteFlowNet3
This repository (<strong>https://github.com/twhui/LiteFlowNet3</strong>) is the offical release of <strong>LiteFlowNet3</strong> for my paper <strong>LiteFlowNet3: Resolving Correspondence Ambiguity for More Accurate Optical Flow Estimation</strong> in ECCV 2020. The pre-print is available <a href="http://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123650171.pdf"> <strong>here</strong></a> and the supplementary material is available <a href="http://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123650171-supp.pdf"> <strong>here</strong></a>. A summary video is available on <a href="https://www.youtube.com/watch?v=Bz7ifJLYR8c"> <strong>YouTube</strong></a>.

</ul>
<table>
<thead>
<tr>
<th align="center"></th>
<th align="center">Sintel Clean Testing Set</th>
<th align="center">Sintel Final Testing Set</th>
<th align="center">KITTI12 Testing Set (Avg-All)</th>
<th align="center">KITTI15 Testing Set (Fl-fg)</th>
<th align="center">Model Size (M)</th> 
<th align="center">Runtime* (ms) GTX 1080</th> 
</tr>
<tr>
<td align="center">LiteFlowNet (CVPR18)</td>
<td align="center">4.54</td>
<td align="center">5.38</td>
<td align="center">1.6</td>
<td align="center">7.99%</td>
<td align="center">5.4</td>
<td align="center">88</td>
</tr> 
<tr>
<td align="center">LiteFlowNet2 (TPAMI20)</td>
<td align="center">3.48</td>
<td align="center">4.69</td>
<td align="center">1.4</td>
<td align="center">7.64%</td>
<td align="center">6.4</td>
<td align="center"><strong>40</strong></td>
</tr> 
<tr>
<td align="center">HD3 (CVPR19)</td>
<td align="center">4.79</td>
<td align="center">4.67</td>
<td align="center">1.4</td>
<td align="center">9.02%</td>
<td align="center">39.9</td>
<td align="center">128</td>
</tr> 
<tr>
<td align="center">IRR-PWC (CVPR19)</td>
<td align="center">3.84</td>
<td align="center">4.58</td>
<td align="center">1.6</td>
<td align="center">7.52%</td>
<td align="center">6.4</td>
<td align="center">180</td>
</tr>
<tr>
<td align="center"><strong>LiteFlowNet3 (ECCV20)</strong></td>
<td align="center"><strong>3.03</strong></td>
<td align="center"><strong>4.53</strong></td>
<td align="center"><strong>1.3</strong></td>
<td align="center"><strong>6.96%</strong></td>
<td align="center"><strong>5.2</strong></td>
<td align="center">59</td>
</tr>    
</tbody></table>

Note: *Runtime is averaged over 100 runs for a Sintel's image pair of size 1024 × 436. 

# License and Citation 
This software and associated documentation files (the "Software"), and the research paper (LiteFlowNet3: Resolving Correspondence Ambiguity for More Accurate Optical Flow Estimation) including but not limited to the figures, and tables (the "Paper") are provided for research purposes only and without any warranty. Any commercial use requires my consent. When using any parts of the Software or the Paper in your work, please cite the following papers:

<pre><code>@InProceedings{hui20liteflownet3,    
 author = {Tak-Wai Hui and Chen Change Loy},    
 title = {{LiteFlowNet3: Resolving Correspondence Ambiguity for More Accurate Optical Flow Estimation}}, 
 journal = {Proceedings of the European Conference on Computer Vision (ECCV)},
 year = {2020},    
}</code></pre>

<pre><code>@InProceedings{hui20liteflownet2,    
 author = {Tak-Wai Hui and Xiaoou Tang and Chen Change Loy},    
 title = {{A Lightweight Optical Flow CNN - Revisiting Data Fidelity and Regularization}, 
 journal = {IEEE Transactions on Pattern Analysis and Machine Intelligence},
 year = {2020},    
 url = {http://mmlab.ie.cuhk.edu.hk/projects/LiteFlowNet/} 
}</code></pre>

<pre><code>@InProceedings{hui18liteflownet,    
 author = {Tak-Wai Hui and Xiaoou Tang and Chen Change Loy},    
 title = {LiteFlowNet: A Lightweight Convolutional Neural Network for Optical Flow Estimation},    
 booktitle  = {Proceedings of IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},    
 year = {2018},    
 pages = {8981--8989},
 url = {http://mmlab.ie.cuhk.edu.hk/projects/LiteFlowNet/} 
}</code></pre>

# Prerequisite and Compiling
LiteFlowNet3 uses the same Caffe package as LiteFlowNet. Please refer to the details in <a href="https://github.com/twhui/LiteFlowNet#Prerequisite"> LiteFlowNet GitHub repository</a>.

# Training
Please refer to the training steps in <a href="https://github.com/twhui/LiteFlowNet#Training"> LiteFlowNet GitHub repository</a> and adopt the training protocols in <a href="http://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123650171.pdf"> LiteFlowNet3 paper</a>.

# Trained models	
To be uploaded.

# Testing 
1. Open the testing folder
<pre><code>$ cd LiteFlowNet3/models/testing</pre></code>

2. Create a soft link in the folder <code>/testing</code>
<pre><code>$ ln -s ../../build/tools bin</code></pre>

3. Replace <code>MODE</code> in <code>./test_MODE.py</code> to <code>batch</code> if all the images has the same resolution (e.g. Sintel dataset), otherwise replace it to <code>iter</code> (e.g. KITTI dataset).

4. Replace <code>MODEL</code> in line 10 (<code>cnn_model = 'MODEL'</code>) of <code>test_MODE.py</code> to one of the trained models (e.g. <code>LiteFlowNet2-ft-sintel</code>).

5. Run the testing script. Flow fields (<code>MODEL</code>-0000000.flo, <code>MODEL</code>-0000001.flo, ... etc) are stored in the folder <code>/testing/results</code> having the same order as the image pair sequence. 
<pre><code>$ test_MODE.py img1_pathList.txt img2_pathList.txt results</code></pre>
