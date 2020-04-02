  afterSubmit(formDatum){
    const promise = new EmberPromise(resolve => {
      if (formDatum.get('additionalInfo').CRSNTB) {
        resolve('CRSNTB');  
      } else {
        resolve();
      }
    });
    promise.then(result => {
      if (result && result.length > 0) {
        if(result === 'CRSNTB') {
          this.get('rdcModalManager')
          .showDialogModal({
            level: 'error',
            title: this.get('i18n').t('ServiceRequest.COMMON.crsMessage.title'),
            message: this.get('i18n').t('ServiceRequest.COMMON.crsMessage.CRSNTB'),
            rejectButtonLabel: this.get('i18n').t('ServiceRequest.COMMON.button.cancel'),
            acceptButtonLabel: this.get('i18n').t('ServiceRequest.COMMON.button.ok')
          })
          .then(() => {
              this.transitionTo('serviceRequest.new-request');
          })
          .catch(() => {});
        }else{
          if (!isFileDelete) this.goToReceiptPage();
        }
      }
      this.enableGoToNext();
    });
  },
  
  
  
    afterSubmit(formDatum) {
    const promise = new EmberPromise(resolve => {
      let isPurposeOfAccBusiness =
      formDatum.get('additionalInfo') && formDatum.get('additionalInfo').isPurposeOfAccBusiness;
      if (!isEmpty(isPurposeOfAccBusiness) && isPurposeOfAccBusiness) {
        resolve('isPurposeOfAccBusiness'); 
      } else if (formDatum.get('additionalInfo').CRSETB) {
        resolve('CRSETB');  
      } else {
        resolve();
      }
    });
    promise.then(result => {
      if (result && result.length > 0) {
        if(result === 'isPurposeOfAccBusiness'){
          this.controller.set('showActionSheet', true);
          this.controller.set('fallbackType', 'isPurposeOfAccBusiness');
          this.controller.set('staticPopup', 'dedupe-failure');
        } else if(result === 'CRSETB') {
          this.get('rdcModalManager')
          .showDialogModal({
            level: 'error',
            title: this.get('i18n').t('ServiceRequest.COMMON.crsMessage.title'),
            message: this.get('i18n').t('ServiceRequest.COMMON.crsMessage.CRSETB'),
            rejectButtonLabel: this.get('i18n').t('ServiceRequest.COMMON.button.cancel'),
            acceptButtonLabel: this.get('i18n').t('ServiceRequest.COMMON.button.ok')
          })
          .then(() => {
              this.transitionTo('serviceRequest.new-request');
          })
          .catch(() => {});
        }
      }
      this.enableGoToNext();
    });
  },
  
  
    afterSubmit(formDatum, isFileDelete){
    const promise = new EmberPromise(resolve => {
      if (formDatum.get('additionalInfo').CRSETB) {
        resolve('CRSETB');  
      } else {
        resolve();
      }
    });
    promise.then(result => {
      if (result && result.length > 0) {
        if(result === 'CRSETB') {
          this.get('rdcModalManager')
          .showDialogModal({
            level: 'error',
            title: this.get('i18n').t('ServiceRequest.COMMON.crsMessage.title'),
            message: this.get('i18n').t('ServiceRequest.COMMON.crsMessage.CRSETB'),
            rejectButtonLabel: this.get('i18n').t('ServiceRequest.COMMON.button.cancel'),
            acceptButtonLabel: this.get('i18n').t('ServiceRequest.COMMON.button.ok')
          })
          .then(() => {
              this.transitionTo('serviceRequest.new-request');
          })
          .catch(() => {});
        }else{
          if (!isFileDelete) this.goToReceiptPage();
        }
      }
      this.enableGoToNext();
    });
  },
