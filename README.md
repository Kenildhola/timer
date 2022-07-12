# timer



***************************** Timer *****************************

/**
     Scroll to Next Cell
     */
    @objc func scrollToNextCell(){
        
        if pageController.currentPage == pageController.numberOfPages - 1 {
            pageController.currentPage = 0
        } else {
            pageController.currentPage += 1
        }
        
        scalingCarousel.scrollToItem(at: IndexPath(row: pageController.currentPage, section: 0), at: .right, animated: true)
    }
    
    /**
     Invokes Timer to start Automatic Animation with repeat enabled
     */
    func startTimer() {
        
        let timer =  Timer.scheduledTimer(timeInterval: 3.3, target: self, selector: #selector(self.scrollToNextCell), userInfo: nil, repeats: true)
    }
    
    
    func collectionView(_ collectionView: UICollectionView, willDisplay cell: UICollectionViewCell, forItemAt indexPath: IndexPath) {

        if collectionView == scalingCarousel {
            self.pageController.currentPage = indexPath.row
        }
        
    }
