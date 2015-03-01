computeVisibleRange算法分析：
第1步，计算出left,right,bottom,top
第2步，计算出numSlots，并除于2赋值给index
第3步，由index得position,判断position是否在第1步计算出的范围内，是的话，就把第2步计算得出的中间的index赋值给firstVisibleSlotIndex，lastVisibleSlotIndex，否则，根据滑动窗口算法改变index直到求组所需index
第4步，在while循环中，用第3步得到的firstVisibleSlotIndex求出position,进行和第2步相反的判断，即position若不在可视范围内，则将相应的index给firstVisibleSlotIndex，否则减firstVisibleSlotIndex,直到找到最小的可视范围内的index作为firstVisibleSlotIndex。
第5步，在while循环中，用第3步得到的lastVisibleSlotIndex求出position,进行和第2步相反的判断，即position若不在可视范围内，则将相应的index给lastVisibleSlotIndex，否则增lastVisibleSlotIndex,直到找到可视范围内的最大的index作为lastVisibleSlotIndex。
第6步，进行firstVisibleSlotIndex，lastVisibleSlotIndex的越界判断。outBufferedVisibleRange对应的是可见的。outBufferedVisibleRange对应的是0～文件夹的最大数。
#### computeVisibleItems算法分析：
第1步由slot计算出position,set,当前set不为空且slot在有效范围，创建bestItems，计算sortedIntersection
第2步计算这个slotindex中的图片数目，取这个文件中的前12张图片加到bestItems。
第3步取bestItems里的图片对应的displayList中的displayItem，并赋值给displayItems数组，同时保存position,及j，j是bestItems数组中一项，范围是0～12。
第4步对于每一个文件夹，要在displayItems里有对应的12项，当文件夹内图片不足12时，余下的用null填充。
当绘制缩略图界面时，有些不同
在第1步中，slotindex不再表示文件夹，这时表示具体某一张图片了，所以由slot得到的set里始终只有1项，且会调ArrayUtils.computeSortedIntersection(visibleItems,items,MAX_ITEMS_PER_SLOT,bestItems,sTempHash);给bestItems赋值，这样第2步就在bestItems加项动作不执行。